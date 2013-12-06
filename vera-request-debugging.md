---
layout: vera
title: Request callback debugging
---

Vera devices support the ability to register a handler that
will be called when a certain URL is requested from the Vera device through
HTTP protocol. You can **register a (callback) function**
using [register_handler](http://wiki.micasaverde.com/index.php/Luup_Lua_extensions#function:_register_handler)
Luup function call.

For example, the call `luup.register_handler("room_request", "room")`
registers a callback function `room_request` that will be
called when a request with `id=lr_[registered_name]` is triggered using
[data_request?id=lr_room](http://device-IP-address:3480/data_request?id=lr_room) URL.

The [callback function](http://wiki.micasaverde.com/index.php/Luup_Declarations#.3Crequest.3E)
gets request, parameters, and outputformat as parameters and returns
the response with an optional content type.

## Debugging Lua code in a request (`register_handler`) callback

ZeroBrane Studio provides [two methods to debug Lua code](vera-remote-debugging.html)
for events triggered from the Vera device:
[scenes](vera-scene-debugging.html),
[plugins](vera-plugin-debugging.html),
[watch](vera-watch-debugging.html),
[request](vera-request-debugging.html), and others.

In this example we will be using the simpler method that doesn't require
specifying the IP address of the computer that runs ZeroBrane Studio:

1. Open a new editor tab in the IDE, add the following code and
save it in a file. In this example I am using device 4 and a
particular serviceId, but you can use whatever device and service you have.

        function room_request (lul_request, lul_parameters, lul_outputformat)
          require('mobdebug').start() --<-- start debugging
          local lul_html = 
            "<head><title>Main</title></head><body>" ..
            "Choose a room:</body>"
          require('mobdebug').done() --<-- stop debugging
          return lul_html, "text/html"
        end
        luup.register_handler("room_request", "room")

2. Start debugging in the IDE by selecting `Project | Start Debugging`.
and then run the script using `Project | Continue`.

3. Point your browser to
[the URL that sends "room" request](http://device-IP-address:3480/data_request?id=lr_room).
Make sure to change the IP address to the address of your Vera device.

You should now see the debugging suspended at the `lul_html` assignment line.
You can then step through the code (and will see the values printed to the
output window), inspect variables, and use other debugging functions.
 
This method only works until the Luup engine is restarted (and in some cases it can be restarted by the Vera device without warning).
If you can't get the debugging started in the IDE, try running step #2 one more time.
