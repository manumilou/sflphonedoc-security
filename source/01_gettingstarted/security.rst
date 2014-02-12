.. _security:



==================
SIP security basics
==================

The first thing to know about SIP security is that there is usually none at all.
By default, **everything is transmitted unencrypted** and readable by any software that can grab traffic between you and your peer. If you are using proxies along the way, each of them may decide to ignore certain security options. 
The second important detail to retain is that SIP security alone (SIPS, SIP-TLS) does not encrypt your communications. SIPS only encrypts the handshake between both peers. To encrypt the media stream (aka, voice) itself, you also need to enable `Secure RTP <http://en.wikipedia.org/wiki/Secure_RTP>`_ (aka, SRTP). 
Likewise, only having SRTP enabled may encrypt your audio but will not obscure information about the call itself (i.e. participants, IP addresses, etc.).

Most registrar and SIP servers have some level of support for security, however, all implementations are not created equal. As of `Asterisk <http://www.asterisk.org/>`_ 1.8 (the default in many server operating systems), some security options are not as well supported as they should be. For a safer system, `Freeswitch <http://www.freeswitch.org>`_ is the best free software option. Asterisk also needs to be recompiled to enable SRTP (see https://projects.savoirfairelinux.com/projects/sflphone/wiki/Security ). This, in turn, will force you to manually update your SIP server everytime a security patch is available, introducing security vulnerabilities of its own.

.. important::

 TODO show security options here

