# [postgresql 快速入门](https://github.com/stormzhai/gitblog/issues/6)

# 1 安装
sudo yum -y install gcc gcc-c++ kernel-devel make zlib zlib-devel libffi-devel openssl-devel git python3-devel postgresql-devel*

sudo yum install -y https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm

sudo yum install -y postgresql14-server

sudo /usr/pgsql-14/bin/postgresql-14-setup initdb
sudo systemctl enable postgresql-14
sudo systemctl start postgresql-14

# 2 远程访问

vim /var/lib/pgsql/14/data/pg_hba.conf
添加
host    all             all             0.0.0.0/0               md5

vim /var/lib/pgsql/14/data/postgresql.conf

listen_addresses = '*'      # 删掉注释

systemctl restart postgresql-14

# 3 客户端访问

psql -U postgres -d test -h 127.0.0.1 -p xxxx

# 4 修改密码

alter user postgres with password ‘此处填写登陆密码’;

# 5 创建角色

create role root; 
alter role root login superuser; 

select rolname from pg_roles;

# 6 基本命令

\q 退出
\l 列出所有库
\c 切换数据库
\du 查看用户
\d 查看表结构
