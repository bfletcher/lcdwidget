lcdwidget
---------
pygtk widget as a rpyc service that simulates a multiline LCD or VFD display. 
The numbers of rows and columns are configurable.

The service exposes one call - print_string()

Whatever string is sent via that service call will be truncated to fit the display
and shown, (character) wrapped to fit the line length.

Usage: lcd_service.py (service_alias_name socket_id)

Defaults:
        service_alias = "LCD1"
        socket_id = 18861

Testing
-------
The test client demonstrates how to call the service. 

Usage: lcd_service.py (socket_id)

The key lines in the client are:
c = rpyc.connect(...)
...
c.root.print_string(...)
