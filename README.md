# Execute actions based on log recods

The main goal of this project is provide [fail2ban](http://www.fail2ban.org) functionality to Windows.

## Configuration
The `lua-spylog` consist of three services.

 * filter - read logs from sources and extract date(optional) and IP and send them to `jail` service.
 * jail - read messages from `filter` service and support time couter. If some counter is reached to
  `maxretry` then jail send message to `action` service.
 * action - read messages from `jail` service and support queue of actions to be done. When it recv new
  message it push 2 new action to queue (ban and unban). Queue is persistent.

All services can be run as separate process or as thread in one multithreaded process.
To run spylog as Windows service you can use [LuaService](https://github.com/moteus/luaservice).
Also works with [nssm](http://nssm.cc) service helper.

## Dependencies
 - [bit32](https://luarocks.org/modules/siffiejoe/bit32)
 - [date](https://luarocks.org/modules/tieske/date)
 - [lluv](https://luarocks.org/modules/moteus/lluv)
 - [lluv-poll-zmq](https://luarocks.org/modules/moteus/lluv-poll-zmq)
 - [lpeg](https://luarocks.org/modules/gvvaughan/lpeg)
 - [Lrexlib-PCRE](https://luarocks.org/modules/rrt/lrexlib-pcre)
 - [lua-cjson](https://luarocks.org/modules/luarocks/lua-cjson)
 - [lua-llthreads2](https://luarocks.org/modules/moteus/lua-llthreads2)
 - [lua-log](https://luarocks.org/modules/moteus/lua-log)
 - [lua-path](https://luarocks.org/modules/moteus/lua-path)
 - [Lua-Sqlite3](https://luarocks.org/modules/moteus/sqlite3)
 - [LuaFileSystem](https://luarocks.org/modules/hisham/luafilesystem)
 - [luuid](https://luarocks.org/modules/luarocks/luuid)
 - [lzmq](https://luarocks.org/modules/moteus/lzmq)
 - [StackTracePlus](https://luarocks.org/modules/ignacio/stacktraceplus)

### To support `mail` action
 - [lluv-ssl](https://luarocks.org/modules/moteus/lluv-ssl)
 - [sendmail](https://luarocks.org/modules/moteus/sendmail)