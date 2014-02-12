.. _configuringsflphonesecurity_f:

Configuring SFLphone security
============================

Configuring a secure `Freeswitch <http://freeswitch.org>`_ account is trivial. 

First, make sure you uploaded the :file:`cacert.pem` and :file:`agent.pem` as described in the earlier steps. Once this is done, create your account using ``Edit > Account > New`` and in the ``Security`` tab, check ``Use TLS transports`` and select ``ZRTP`` in ``SRTP key exchange``.

Now, in the ``Edit`` dialog, add both your :file:`cacert.pem` and :file:`agent.pem` and press ``OK``.
