Installing MemSQL Ops in /var/lib/memsql-ops

Creating a memsql user

Setting up permissions

Creating an init script so that MemSQL Ops runs on startup

Creating a symlink to MemSQL Ops at /usr/bin/memsql-ops

Creating a symlink to a MemSQL client at /usr/bin/memsql

Successfully installed MemSQL Ops!

You can install MemSQL across multiple machines

using the MemSQL Ops Web UI.

2017-10-10 19:27:35: Jddfb05 [INFO] Deploying MemSQL to 127.0.0.1:3306

2017-10-10 19:27:35: J0d2c0d [INFO] Deploying MemSQL to 127.0.0.1:3307

2017-10-10 19:31:45: J0d2c0d [INFO] Downloading MemSQL: 100.00%

2017-10-10 19:31:45: J0d2c0d [INFO] Installing MemSQL

2017-10-10 19:31:45: Jddfb05 [INFO] Downloading MemSQL: 100.00%

2017-10-10 19:31:45: Jddfb05 [INFO] Installing MemSQL

2017-10-10 19:31:51: Jddfb05 [INFO] Finishing MemSQL Install

2017-10-10 19:31:52: J0d2c0d [INFO] Finishing MemSQL Install

2017-10-10 19:31:52: Jddfb05 [INFO] Successfully deployed MemSQL with role MASTER at 127.0.0.1:3306

2017-10-10 19:31:52: J0d2c0d [INFO] Successfully deployed MemSQL with role LEAF at 127.0.0.1:3307

Waiting for MemSQL to start…

A MemSQL cluster is now deployed to your local host. Run the command

below to connect to MemSQL with the mysql client:

$ memsql -P 3306

You can setup, manage and monitor MemSQL with the MemSQL Ops

web UI on port 9000\. Make sure that port 9000 is open in your

firewall or security group.