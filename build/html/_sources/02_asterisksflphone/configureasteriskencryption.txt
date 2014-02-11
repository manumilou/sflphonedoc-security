.. _configuringasteriskencryption:

Configuring Asterisk encryption
==============================

In this part, we will use TLS to encrypt the streams.

::

 sudo su -
 apt-get install openssl
 mkdir /etc/certs
 cd /etc/certs/
 wget https://raw.github.com/rillian/asterisk-opus/master/contrib/scripts/ast_tls_cert
 sh ast_tls_cert -C pbx.MyHostName -O "NSA proof(?) server" -d /etc/certs/
 #Now fill out the form.
 sh ast_tls_cert -m client -c /etc/certs/ca.crt -k /etc/certs/ca.key -C mynsauser.MyHostName -O "NSA proof(?) server" -d /etc/certs -o mynsauser
 chown asterisk:asterisk ./ -R
 ls

Now, let's take a step back. This howto has assumed the same computer as server and client for simplicity's sake. In a real-world context, this will rarely be the case. So you will have to safely upload the certificates to the client computer. To do this, the "scp" command allows you to upload the key over an encrypted connection. In our case, you can simply copy them using "cp" as it doesn't change anything.

::

 scp mynsauser.pem username@hostname:/tmp/
 scp ca.crt username@hostname:/tmp/

Now, Asterisk need to be configured to use this certificate for encrypted calls. Backup your current /etc/asterisk/sip.conf, then open sip.conf and replace its contents with:

::

 [general]
 context=internal
 allowguest=no
 allowsubscribe=yes
 allowoverlap=no
 bindport=5060
 bindaddr=0.0.0.0      ;192.168.48.213
 tlsbindaddr=0.0.0.0   ;192.168.48.213
 srvlookup=no
 disallow=all
 allow=ulaw
 allow=g722
 allow=alaw
 allow=gsm
 alwaysauthreject=yes
 canreinvite=no
 ;nat=yes
 session-timers=refuse
 localnet=192.168.48.0/255.255.252.0
 tlsenable=yes
 tlscertfile=/etc/certs/asterisk.pem
 tlscafile=/etc/certs/ca.crt
 tlscipher=TLSv1
 ;tlsclientmethod=tlsv1
 tlsdontverifyserver=no
 tlsbindaddr=0.0.0.0
 
 [777]
 callerid=NSA
 type=friend
 secret=nsa
 host=dynamic
 transport=tls 
 port=5061
 context=internal
 dtmfmode=rfc2833
 insecure = invite,port
 nat = yes

 [888]
 callerid=NSA
 type=friend
 secret=nsa
 host=dynamic
 transport=tls 
 port=5061
 context=internal
 dtmfmode=rfc2833
 insecure = invite,port
 nat = yes

 [999]
 callerid=PLAY
 type=friend
 secret=play
 host=dynamic
 transport=tls
 port=5061
 context=local
 dtmfmode=rfc2833
 ;insecure = invite,port
 nat = yes

And in extensions.conf, in the "[local]" section, add:

::

 exten => 999,1,Answer
 exten => 999,2,Playback(tt-weasels)
 exten => 999,3,Wait(10)
 exten => 999,4,Hangup

Now, run the "rasterisk" command and type:

::

 sip reload
 dialplan reload

Asterisk should now be using TLS for message passing. Note that the stream itself is not yet encrypted.
