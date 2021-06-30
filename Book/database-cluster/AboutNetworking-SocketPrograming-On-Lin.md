# PgBouncer connect to PostgreSQL : 
- Link : [https://www.postgresql.org/docs/current/protocol-flow.html](https://www.postgresql.org/docs/current/protocol-flow.html) at the startup.

# Multi Statements In A Simple Query : 
```psql
INSERT INTO MY_TABLE VALUES(1);
SELECT 1/0;
INSERT INTO MY_TABLE VALUES(2);
```

> Gonna force roll back of the first ```INSERT```.  Cuz of the message is abandoned at the first error, the second ```INSERT``` is never attempted at all.

```
BEGIN;
INSERT INTO mytable VALUES(1);
COMMIT;
INSERT INTO mytable VALUES(2);
SELECT 1/0;
```

> Because of we ```COMMIT``` after the first ```INSERT``` so will roll back the second ```INSERT```, but not the first one.


# Message define :
```python
PSQL_FE_MESSAGES = {

'p': "Password message",

'Q': "Simple query",

'P': "Parse",

'B': "Bind",

'E': "Execute",

'D': "Describe",

'C': "Close",

'H': "Flush",

'S': "Sync",

'F': "Function call",

'd': "Copy data",

'c': "Copy completion",

'f': "Copy failure",

'X': "Termination",

}
```
# Regular package :

|  char tag | int32 len  |  payload |
|---|---|---|---|---|

> The exception is the startup package, which starts with the length followed
|  int32 len| int32 len  |  payload |
|---|---|---|---|---|
# Setup connection 

# reference :
- [https://www.pgcon.org/2014/schedule/attachments/330_postgres-for-the-wire.pdf](https://www.pgcon.org/2014/schedule/attachments/330_postgres-for-the-wire.pdf)

> This is include notice request + authenticate request.

<img src="https://i.imgur.com/vCp28Nb.png">


> Simple query  (select  query)

<img src="https://i.imgur.com/PNAIY0l.png" />
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkwMjY3OTY1OCwxODkyMzU3Mzk1LC0xNz
U2OTczOSwtMzA2NDEyMjUyLDU4Mjk1NDg0Nyw3MzA5OTgxMTZd
fQ==
-->