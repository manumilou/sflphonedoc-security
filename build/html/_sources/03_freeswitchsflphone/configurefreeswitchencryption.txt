.. _configurefreeswitchencryption:

Configuring Freeswitch security
==============================

To have an overview of SIP security, please read ---------TODO add the link---------

::

 cd /usr/local/freeswitch/bin
 sudo ./gentls_cert setup -cn 127.0.0.1 -alt DNS:localhost -org 127.0.0.1
 sudo ./gentls_cert create_server -cn 127.0.0.1 -alt DNS:localhost -org 127.0.0.1

This will generate a self signed certificate in /usr/local/freeswitch/conf/ssl/CA/cakey.pem. Self signed certificates are not entirely secure and void the chain of trust. If you want care about security, please generate a certificate signed by an authority.

Now, in */usr/local/freeswitch/conf/vars.xml*, enable TLS:

**Original:**

<X-PRE-PROCESS cmd="set" data="sip_tls_version=tlsv1"/>

<!-- Internal SIP Profile -->
<X-PRE-PROCESS cmd="set" data="internal_auth_calls=true"/>
<X-PRE-PROCESS cmd="set" data="internal_sip_port=5060"/>
<X-PRE-PROCESS cmd="set" data="internal_tls_port=5061"/>
<X-PRE-PROCESS cmd="set" data="internal_ssl_enable=false"/>

<!-- External SIP Profile -->
<X-PRE-PROCESS cmd="set" data="external_auth_calls=false"/>
<X-PRE-PROCESS cmd="set" data="external_sip_port=5080"/>
<X-PRE-PROCESS cmd="set" data="external_tls_port=5081"/>
<X-PRE-PROCESS cmd="set" data="external_ssl_enable=false"/>

**New:**

<X-PRE-PROCESS cmd="set" data="sip_tls_version=tlsv1"/>

<!-- Internal SIP Profile -->
<X-PRE-PROCESS cmd="set" data="internal_auth_calls=true"/>
<X-PRE-PROCESS cmd="set" data="internal_sip_port=5060"/>
<X-PRE-PROCESS cmd="set" data="internal_tls_port=5061"/>
<X-PRE-PROCESS cmd="set" data="internal_ssl_enable=true"/>
<X-PRE-PROCESS cmd="set" data="internal_ssl_dir=$${base_dir}/conf/ssl"/>

<!-- External SIP Profile -->
<X-PRE-PROCESS cmd="set" data="external_auth_calls=false"/>
<X-PRE-PROCESS cmd="set" data="external_sip_port=5080"/>
<X-PRE-PROCESS cmd="set" data="external_tls_port=5081"/>
<X-PRE-PROCESS cmd="set" data="external_ssl_enable=true"/>
<X-PRE-PROCESS cmd="set" data="external_ssl_dir=$${base_dir}/conf/ssl"/>

Now, in the freeswitch shell, execute:

::

 reloadxml

Back in */usr/local/freeswitch/bin*, it is now time to create certificate for users:

::

 sudo ./gentls_cert create_client -cn 1002 -out 1002.pem

Be sure to copy/scp the following certificates to all relevants users.

Now, lets take a step back. This how to is always using the same computer as server and client for simplicity purpose. In a real context, this will rarely be the case. So you will have to safely upload the certificates to the client computer. To do this, the "scp" command allow you to create an encrypted upload of the key, thus, invulnerable to man in the middle attack. In this case, you can copy them using "cp" as it doesn't change anything.

::

 scp /usr/local/freeswitch/conf/ssl/CA/cacert.pem username@hostname:/home/username/
 scp /usr/local/freeswitch/conf/ssl/agent.pem username@hostname:/home/username/

If you use an alternate upload method, please double check if the target file owned by the same used as the sflphone process (usually your current username) and have "600" permissions. The "scp" lines will automatically do that for you.

Optional:
~~~~~~~~

In this how-to, we run FreeSwitch as root. This, of course, as FreeSwitch is a network facing application, is a potential attack vector. If you change freeswitch user, do not forget to use:

::

 cd /usr/local/freeswitch/
 find -iname conf/ssl/ | xargs chown myfreeswitchuser:myfreeswitchuser

Reference: http://wiki.freeswitch.org/wiki/SIP_TLS

