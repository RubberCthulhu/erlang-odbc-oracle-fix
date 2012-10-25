erlang-odbc-oracle-fix
======================

It's a fix for erlang odbc module which solves the problem with setup autocommit mode for connections established by Oracle ODBC driver in Linux.

The issue: Oracle ODBC driver for Linux ignores setup autocommit mode during driver initialization before a connection to database has been established.

Solution: set autocommit mode after a connection to database has been established.

