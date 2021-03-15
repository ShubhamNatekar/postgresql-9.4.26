# How to setup postgres from source code

## Installetion :
- After downloding the [postgres source code](https://www.postgresql.org/ftp/source/v9.4.26/)  run the following cmds:
- `    sudo ./configure `
- `    sudo make `
- `    sudo passwd root ` (Change root password)
- `    su ` 
- `    make install  `
- `    adduser postgres    ` (create user for postgres)
- `    sudo passwd postgres ` (Change postgres password)
- `    sudo mkdir /usr/local/pgsql/data   ` (we can also create some other directory for data eg. mkdir ~/mycluster)
- `    sudo chown postgres /usr/local/pgsql/data `
- `    su postgres `

## Configuration :
-   Open 'vim ~/.bashrc' file and add below lines.
``` 
    export LD_LIBRARY_PATH=/usr/local/pgsql/lib  
    export PATH=/usr/local/pgsql/bin:$PATH 
```
- ` export PGDATA=/usr/local/pgsql/data `
- ` source ~/.bashrc ` (Reload shell)

**NOTE:** This ".bashrc" file is diffrent from you local machine make sure you are login with postgres user.

### Now you can directly use psql cmds :
- ` initdb -D /usr/local/pgsql/data ` (The "-D" option specifies the location where the data will be stored.)
- ` postgres -D /usr/local/pgsql/data >logfile 2>&1 & `
- eg. ` initdb -D /usr/local/pgsql/data `
- eg. ` postgres -D /usr/local/pgsql/data >logfile 2>&1 & `
- ` pg_ctl start `     (start psql server)

### To check server is running run below cmd: 
- ` pg_ctl status `         
        pg_ctl: server is running (PID: 10246)
        /usr/local/pgsql/bin/postgres

- ` psql --version`
- ` psql ` (optional: psql -U shubham -d shubham)

## To work on psql everytime run only following cmds:
- ` su postgres`
- ` pg_ctl start ` (To start the server) or ` pg_ctl restart ` (To restart server )
- ` psql `
