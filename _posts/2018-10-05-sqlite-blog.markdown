---
layout:     post
title:      "iOS数据库之FMDB"
subtitle:   " \"Exmple for FMDB\""
date:       2018-10-05 12:00:00
author:     "Wangpt"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - OC
    - FMDB

---

> “数据库的基本使用”


## 简介
*通过操作数据库进行数据的增删改查功能*

---

## FMDB的使用

### 创建数据库

```objc
+ (void)initialize{
    NSString *fileName = [[NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES)lastObject] stringByAppendingPathComponent:DBNAME];
    _queue = [FMDatabaseQueue databaseQueueWithPath:fileName];
    [_queue inDatabase:^(FMDatabase *db) {
        BOOL b = [db executeUpdate:@"CREATE TABLE IF NOT EXISTS People (id text,info blob)"];
        NSLog(@"create table is %d",b);
    }];
}

```
### 存储数据
1.对象序列号

*存储自定义对象需要进行序列号操作*

```objc
@interface PersonInfoModel : NSObject <NSCoding>
@property (nonatomic, strong) NSString *name;
@property (nonatomic, strong) NSString *sex;
@property (nonatomic, assign) NSInteger age;
@end
```

```
@implementation PersonInfoModel
- (instancetype)initWithCoder:(NSCoder *)aDecoder{
    if (self = [super init])
    {
        self.name = [aDecoder decodeObjectForKey:@"name"];
        self.sex = [aDecoder decodeObjectForKey:@"sex"];
        self.age = [aDecoder decodeIntegerForKey:@"age"];
    }
    return self;
    
}

- (void)encodeWithCoder:(NSCoder *)aCoder{
    [aCoder encodeObject:self.name forKey:@"name"];
    [aCoder encodeObject:self.sex forKey:@"sex"];
    [aCoder encodeInteger:self.age forKey:@"age"];
}
@end
```

2.对象存储

```objc
+ (void)qunueInsertPeople:(PersonModel *)people{
    NSData *infoData = [NSKeyedArchiver archivedDataWithRootObject:people.infoModel];
    [_queue inDatabase:^(FMDatabase *db) {
        BOOL insert = [db executeUpdate:@"INSERT INTO People (id, info) VALUES (?,?)",people.id,infoData];
        if (insert) {
            NSLog(@"添加成员成功！！");
        }else{
            NSLog(@"添加成员失败！！");
        }
    }];
}
```

### 删除数据

```objc
+ (BOOL)qunueDeletePeople:(NSString *)userId{
    NSString *sql = [NSString stringWithFormat:@"DELETE FROM People WHERE id = %@",userId];
    return [self executeUpdate:sql];
}
```
### 修改数据

```objc
+ (void)qunueUpdatePeople:(PersonModel *)people{
    NSData *infoData = [NSKeyedArchiver archivedDataWithRootObject:people.infoModel];
    NSString *sql = @"UPDATE People SET id = ? , info = ? WHERE id = ?";
    [_queue inDatabase:^(FMDatabase *db) {
        BOOL insert = [db executeUpdate:sql,people.id.stringValue,infoData,people.id];
        if (insert) {
            NSLog(@"修改成员成功！！");
        }else{
            NSLog(@"修改成员失败！！");
        }
    }];
}
```

### 查找数据

```objc
+ (NSArray *)qunueGetPeople{
    __block NSMutableArray *dataArray = @[].mutableCopy;
    NSString *sql = [NSString stringWithFormat:@"SELECT *FROM People"];
    [self executeQuery:sql queryResBlock:^(FMResultSet *rs) {
        while ([rs next]) {
            PersonModel *entity = [[PersonModel alloc]init];;
            NSString *userId = [rs stringForColumn:@"id"];
            entity.id =[NSNumber numberWithInteger:userId.integerValue];
            NSData *infoData = [rs dataForColumn:@"info"];
            PersonInfoModel *infoModel = [NSKeyedUnarchiver unarchiveObjectWithData:infoData];
            entity.infoModel =infoModel;
            [dataArray addObject:entity];
        }
        [rs close];
    }];
    return dataArray;
}
```
### 追加字段

```objc
+ (void)columnExists{
    [_queue inDatabase:^(FMDatabase *db) {
        if (![db columnExists:@"mesType" inTableWithName:@"People"]){
            NSString *alertStr = [NSString stringWithFormat:@"ALTER TABLE %@ ADD %@ INTEGER",@"People",@"mesType"];
            BOOL worked = [db executeUpdate:alertStr];
            if(worked){
                NSLog(@"插入成功");
            }else{
                NSLog(@"插入失败");
            }
        }
    }];
}
```

##  代码下载

[TJCache](https://github.com/wangpt/TJCache)


