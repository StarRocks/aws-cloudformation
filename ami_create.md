#### 安装 jdk 1.8
#### 创建 /home/ec2-user/tool/cluster-tool.py
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb
import sys
import time
import os

time.sleep(30)
db = MySQLdb.connect(host = '127.0.0.1', user = 'root', passwd = '', port = 9030, connect_timeout=10)
cursor = db.cursor()
for index in range(len(sys.argv)):
    if index == 0:
        continue
    if sys.argv[index] != '0.0.0.0':
        cursor.execute("ALTER SYSTEM ADD BACKEND '%s:9050'"%sys.argv[index])
data = cursor.fetchone()
db.close()
```
#### 安装 MySQL-python
yum install MySQL-python.x86_64

#### 下载 starrocks 安装包