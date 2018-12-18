##Basics
Connection String  
```
HOST = tesla.epa.gov
PORT = 3306
USERNAME = yourusername
PASSWORD = yourpassword
```
Extra Params to set
```
use_unicode = True
charset = utf8
```

Change Password
```SQL
SET PASSWORD = "MyPassword"
```

##Connecting with Python 3.x
Package to install for Python 3.x = pymysql https://github.com/PyMySQL/PyMySQL  
Example:
```python
import pymysql.cursors

# Connect to the database
connection = pymysql.connect(host='localhost',
                             user='user',
                             password='passwd',
                             db='db',
                             charset='utf8mb4',
                             cursorclass=pymysql.cursors.DictCursor)
try:
    with connection.cursor() as cursor:
        # Read a single record
        sql = "SELECT * FROM prod_factotum"
        cursor.execute(sql)
        result = cursor.fetchone()
        print(result)
finally:
    connection.close()
```
##Connecting with R
Good article on HOWTO at https://www.r-bloggers.com/accessing-mysql-through-r/
```R
install.packages("RMySQL")
library(RMySQL)

mydb = dbConnect(MySQL(), user='user', password='password', dbname='database_name', host='host')

dbListTables(mydb)
dbListFields(mydb, 'some_table')


rs = dbSendQuery(mydb, "select * from some_table LIMIT 10")
data = fetch(rs, n=-1)
```


