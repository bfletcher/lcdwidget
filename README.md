lcdwidget
---------
pygtk widget that simulates a multiline LCD or VFD character display. 
The numbers of rows and columns are configurable.
The widget starts a corresponding rpyc service with a socket_id and a
name. 

The default socket id should work fine. If you create multiple widgets
they'll need separate socket ids.

The service exposes one call - print_string()

Whatever string is sent via the corresponding rpyc service call will be truncated 
to fit the display and shown, (character) wrapped to fit the line length.

Usage: lcd_service.py (service_alias_name socket_id)

Defaults:
        service_alias = "LCD1"
        socket_id = 18861

Testing
-------
The test client demonstrates how to call the service. 

Usage: lcd_client.py (socket_id)

The socket_id should be the same as the service you're trying to connect to.

The key lines in the client are:
c = rpyc.connect(...)
...
c.root.print_string(...)

Notes
-----
The service_alias_name string sets the window banner name and also appears in any 
registry of rpyc services (entirely optional).

Acknowledgements
----------------
The actual (& awesome) display came from a gist by John Stowers - https://github.com/nzjrs
