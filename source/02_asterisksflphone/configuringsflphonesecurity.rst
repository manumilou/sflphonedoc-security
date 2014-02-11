.. _configuringsflphonesecurity:

Configuring SFLphone security
============================

**Prerequisites:** You have both ca.crt and the .pem certificates

For Asterisk to encrypt your stream, select:

* Edit -> Account -> Your account -> Security -> SRTP key exchanges and Select ZRTP (Asterisk need to be compiled with SRTP support). Also select "Use TLS transports"
 
* In the "Advanced" tab, set your ca.crt as authority and .pem as user certificate.
* Uncheck "Verify incoming certificate (as a server)"
 
* Click on apply
 
You are now done, please note that this setup is still vulnerable to man in the middle attack, but not to packet sniffers.
