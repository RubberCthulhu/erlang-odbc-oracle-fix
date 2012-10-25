erlang-odbc-oracle-fix
======================

It's a fix for erlang odbc module which solves the problem with setup autocommit mode for connections established by Oracle ODBC driver in Linux.

Issue
-----

Oracle ODBC driver for Linux ignores setup autocommit mode during driver initialization before a connection to database has been established.

Solution
--------

This fix set autocommit mode after a connection to database has been established. The patch changes only C source file odbcserver.c and don't change any erlang source files of odbc module.

I created two patches for different Erlang OTP distributions:
* otp_R14B04_odbc-oracle-fix.patch is for versions R14B04, R15B, R15B01 (File odbcserver.c is the same in all of these distributions).
* otp_R15B02_odbc-oracle-fix.patch is for version R15B02.

How to install
--------------

To install fixed odbc erlang module:
* Download a sufficient patch file.
* Download tarball of Erlang OTP source code from http://erlang.org.
* Extract tarball:

```
tar xzvf otp_src_%VERSION%.tar.gz
```

* Change directory to Erlang OTP distribution:

```
cd otp_src_%VERION%
```

* Apply a patch:

```
patch -p1 </path/to/patch/file/otp_%VERSION%_odbc-oracle-fix.patch
```

* Compile sources:

```
./configure
make
```

* If you want to install entire distribution do:

```
make install
```

* If you want only to fix odbc module in existed Erlang OTP installation copy odbcserver executable to sufficient directory in your Erlang OTP:

```
sudo cp ./lib/odbc/priv/bin/odbcserver /erlang/otp/path/lib/odbc/priv/bin/
```

NOTE: check pathes to odbcserver file carefully - they may be different a little in your case.

Contacts
--------

alevandal@gmail.com.


