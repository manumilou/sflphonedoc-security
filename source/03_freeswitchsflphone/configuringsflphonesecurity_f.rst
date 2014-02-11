.. _configuringsflphonesecurity_f:

Configuring SFLphone security
============================

Configuring a secure Freeswitch account is trivial. 

First, make sure you uploaded the "cacert.pem" and "agent.pem" as described in the earlier steps. Once this is done, create your account using Edit->Account->New and in the "Security" tab, check "Use TLS transports" and select "ZRTP" in "SRTP key exchange".

Now, in the "Edit" dialog, add both your "cacert.pem" and "agent.pem" and press ok.
