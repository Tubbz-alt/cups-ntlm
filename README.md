cups-ntlm
=========

This is a CUPS backend for printing via IPP(S) to a Windows print server using NTLM authentication.

Requires: 
- [pkipplib](http://pypi.python.org/pypi/pkipplib) 
- [python-ntlm](http://code.google.com/p/python-ntlm/)
 

If using Python < 2.5, also requires [hashlib](http://pypi.python.org/pypi/hashlib), compiled with OpenSSL libraries in order to provide the MD4 algorithm.

In order to use this backend, copy it to the CUPS backend folder (/usr/lib/cups/backend) named "ntlm" (rename if necessary), make sure it's owned by root user and group, and make sure the permissions on the file are at least 500 (it should at least be readable and executable by owner).  Then, restart the CUPS service.

To add a printer, get the IPP URI of the printer for the Windows server, and change it so it's in the following format:

    ntlm://DOMAIN\username:password@print-server:port/resource?option=value

All IPP options are valid, and an additional option, "debug," has been added. To use debugging, set the debug value to "true".

Here's an example of a valid printer URI for the NTLM backend:

    ntlm://MYDOMAIN\myuser:mypass@my-print-server.example.com:443/printers/myprinter/.printer?encryption=always&waitjob=false&debug=true

See here for more information on IPP printer URIs:
http://www.cups.org/documentation.php/doc-1.4/network.html#IPP
