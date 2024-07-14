## 后端设置

### 克隆和检出项目代码
```bash
git clone https://gitee.com/y_project/RuoYi.git
cd RuoYi
git tag
git checkout v3.8.3
```

### 安装和配置 MySQL
```bash
sudo apt update
sudo apt install mysql-server
sudo mysql_secure_installation
sudo systemctl status mysql.service
```

### MySQL 配置
```bash
mysql -u root -p

# 创建新用户
CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';

# 刷新权限
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

# 创建数据库
CREATE DATABASE ry-vue;

# 退出 MySQL
quit;
```

### 导入数据脚本
```bash
mysql -u root -p ry-vue < ry_2021xxxx.sql
mysql -u root -p ry-vue < quartz.sql

# 重启数据库
sudo systemctl restart mysql

# 增加数据库安全性（可选）
sudo mysql_secure_installation
```

### 配置 Spring 数据源
在 `application.yml` 文件中配置数据库连接：
```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/ry?useUnicode=true&characterEncoding=utf-8&serverTimezone=Asia/Shanghai
    username: root
    password: 123  # 修改为你设置的 MySQL root 用户密码
```

### 打包和运行后端项目
```bash
# 返回到项目根目录
cd ..

# 执行 Maven 打包
mvn package

# 运行 jar 包
java -jar RuoYi/ruoyi-admin/target/ruoyi-admin-4.7.8.jar
```

## 前端设置

### 进入项目目录并安装依赖
```bash
# 进入项目目录
cd ruoyi-ui

# 安装依赖
npm install

# 使用指定的 registry 加快安装速度
npm install --registry=https://registry.npmmirror.com
```

### 启动前端项目
如果 `npm install` 仍然很慢，可以执行以下命令：
```bash
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```
然后启动开发服务器：
```bash
npm run dev
```

完成以上步骤后，前端和后端项目将分别启动并运行。