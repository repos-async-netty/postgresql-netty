# postgresql-netty - an async Netty/NIO based PostgreSQL driver written in Scala

The main goal of this project is to implement a performant and fully functional async PostgreSQL driver. This project
has no interest in JDBC, it's supposed to be a clean room implementation for people interested in talking directly
to PostgreSQL.

[PostgreSQL protocol information and definition can be found here](http://www.postgresql.org/docs/devel/static/protocol.html)

## What can it do now?

- connect to a database without authentication (it only connects if it gets an AuthenticationOk message)
- receive parameters
- receive database notices
- execute direct queries (without portals/prepared statements)
- parses all basic PostgreSQL types, other types are parsed as string
- date, time and timestamp types are handled as JodaTime objects and **not** as **java.util.Date** objects

## What is missing?

- portals/prepared statements
- stored procedures
- authentication mechanisms
- benchmarks and more testing

## What are the design goals?

- fast, fast and faster
- small memory footprint
- avoid copying data as much as possible (we're always trying to use wrap and slice on buffers)
- easy to use, call a method, get a future or a callback and be happy
- never, ever, block (the only real blocking right now is at the connection pool)
- all features covered by tests

## How can I help?

- checkout the source code
- find bugs, find places where performance can be improved
- check the **What is missing** piece
- send a pull request with specs

This project is freely available under the MIT licence, use it at your own risk.