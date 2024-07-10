# 安装ruoyi-4.7.8

### 1. 拉取源码

```
git clone https://gitee.com/y_project/RuoYi.git
cd RuoYi
```

### 2. 查看可用的版本标签

```
git tag
```

### 3. 切换到特定版本

假设选择版本 `v4.7.8`：

```
git checkout v4.7.8
```

### 4. 安装并配置 MySQL 数据库

```
sudo apt update
sudo apt install mysql-server
sudo mysql_secure_installation
sudo systemctl status mysql.service
```

### 5. 登录 MySQL 并创建新用户和修改密码

```
mysql -u root -p

# 创建新用户
CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;

# 修改 root 用户密码
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123';
FLUSH PRIVILEGES;

# 修改密码规则
SET GLOBAL validate_password_policy=LOW;
SET GLOBAL validate_password_length=6;
SET GLOBAL validate_password_mixed_case_count=0;
SET GLOBAL validate_password_number_count=0;
SET GLOBAL validate_password_special_char_count=0;
```

### 6. 创建数据库并导入数据脚本

```
# 创建数据库
CREATE DATABASE ry;

# 退出 MySQL
exit;

# 导入数据脚本（假设脚本在当前目录下）
mysql -u root -p ry < ry_2021xxxx.sql
mysql -u root -p ry < quartz.sql
```

### 7. 修改配置文件

编辑 `resources` 目录下的 `application.yml` 文件，修改端口和数据库密码：

```
server:
  port: 8080  # 修改为未占用的端口，例如8080

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/ry?useUnicode=true&characterEncoding=utf-8&serverTimezone=Asia/Shanghai
    username: root
    password: 123  # 修改为你设置的 MySQL root 用户密码
```

### 8. 打包并运行

```
# 返回到项目根目录
cd ..

# 执行 Maven 打包
mvn package

# 运行 jar 包
java -jar RuoYi/ruoyi-admin/target/ruoyi-admin-4.7.8.jar
```

### 9. 访问应用

在浏览器中访问：`http://localhost:8080`，应该可以看到 RuoYi 的登录页面。
