### Install PostgreSQL on Ubuntu

https://www.postgresql.org/download/linux/ubuntu/

> After installation automatically a new user "postgres" will be created in your system.

### Login to "postgres" user

```bash
rajan@ubuntu:~$ sudo -i -u postgres
postgres@ubuntu:~$ 
```

### Create new PostgreSQL user

> Interactive mode will ask you about user privileges like this (choose according to your need)
>
> ```bash
> Shall the new role be a superuser? (y/n) n
> Shall the new role be allowed to create databases? (y/n) n
> Shall the new role be allowed to create more new roles? (y/n) n
> ```

```bash
postgres@ubuntu:~$ createuser 'testUser' --interactive
```

### Use PostgreSQL prompt

```bash
postgres@ubuntu:~$ psql
```

### Check Users/Roles

Check if user created by you exists or not.

```postgresql
postgres=# SELECT rolname FROM pg_roles;
/* OR use */
postgres=# \du
```

### Create new Database

```postgresql
postgres=# CREATE DATABASE testDB;
/* list databases */
postgres=# SELECT datname FROM pg_database;
/* OR use */
postgres=# \l
```

### Access database using newly created user

> First exit from PostgreSQL prmpt using `\q`

```bash
postgres@ubuntu:~$ psql -U "testUser" -h 127.0.0.1 testDB
```

Your prompt will look like this

> With user name you may see "=>" instead of "=#", it means logged in user is not a superuser

```postgresql
testUser=>
```

---

### Connection URL for web app

> Username = testUser, Password = 123456 and Database = testDB

```postgresql://testUser:123456@127.0.0.1:5432/testDB```

You may need to specify connection driver, for example

```postgresql+psycopg://testUser:123456@127.0.0.1:5432/testDB```