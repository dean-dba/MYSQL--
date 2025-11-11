# MySQL 用户与SSL

#### MySQL 从8.0开始在用户安全、传输安全方面，进行了很多的改进，下面将对这些改进进行总结性梳理

- **密码验证插件由mysql_native_password改为caching_sha2_password**
- **增加了密码强度验证插件**
- **增加了角色功能**
- **增加了新旧密码优雅替换功能**
- **增加了用户与用户之间授权功能**
- **增加了部分权限回收功能**
- **增加了同一账户双密码功能，可以使旧密码优雅的下线**
- **增加了多重密码验证功能**
- **服务端默认开启SSL，但不强制客户端开启SSL**

创建用户，并授权
```
CREATE USER 'jeffrey'@'localhost' IDENTIFIED BY 'password';
GRANT SELECT ON app_db.* TO 'jeffrey'@'localhost';
```

修改用户密码
```
ALTER USER 'jeffrey'@'localhost' IDENTIFIED BY 'password';
```

查看用户及权限
```
set print_identified_with_as_hex = on;
SHOW CREATE USER 'jeffrey'@'localhost';
SHOW GRANTS FOR 'jeffrey'@'localhost';
```

