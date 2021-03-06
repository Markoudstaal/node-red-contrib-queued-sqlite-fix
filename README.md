node-red-contrib-queued-sqlite-fix
====================

This repository is a fix for [node-red-contrib-queued-sqlite](https://github.com/DuimTechniek/node-red-contrib-queued-sqlite). As that package hasn't been updated in 2 years and that package now fails to install.

A Node-Red node to read and write a local sqlite database.

Based on the basic node-red-sqlite, but this allows queueing of messages and dynamic databases.

Install
-------

Run the following command in your Node-RED user directory - typically `~/.node-red`

    npm i --unsafe-perm node-red-contrib-queued-sqlite


Usage
-----

Allows basic access to a Sqlite database.

This node uses the <b>db.all</b> operation against the configured database.
This does allow INSERTS, UPDATES and DELETES.

By it's very nature it is SQL injection... so *be careful* out there...

`msg.topic` must hold the <i>query</i> for the database, and the result is returned in `msg.payload`.

All queries are automatically queued and dequeued per database.

Typically the returned payload will be an array of the result rows, (or an error).

You can load sqlite extensions by inputting a <code>msg.extension</code> property containing the full path and filename.

You can choose a database in the configuration or provide it in `msg.database`.

The reconnect timeout in milliseconds can be changed by adding a line to **settings.js**

    sqliteReconnectTime: 20000,
