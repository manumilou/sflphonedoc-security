.. _configuringsflphonesecurity:

Configuring SFLphone security
============================

.. important::

 **Prerequisites:** You have both ca.crt and the .pem certificates

For `Asterisk <http://asterisk.org>`_ to **encrypt your stream**, select:

* In ``Edit > Account > Your account > Security``, select ``ZRTP`` in ``SRTP key exchanges`` (`Asterisk <http://asterisk.org>`_ need to be compiled with SRTP support). Also select ``Use TLS transports``.
 
* In the ``Advanced`` tab, set your ca.crt as authority and .pem as user certificate.
* Uncheck ``Verify incoming certificate (as a server)``
 
* Click on ``Apply``
 
You are now done!


.. warning::
 
 Please note that this setup is still vulnerable to `Man-in-the-middle attack <http://en.wikipedia.org/wiki/Man-in-the-middle_attack>`_, but not to packet sniffers.
