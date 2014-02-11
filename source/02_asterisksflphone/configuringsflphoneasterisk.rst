.. _configuringsflphoneasterisk:

Configuring SFLphone with Asterisk
==================================

Once this is done, execute "sflphone-client-gnome". A configuration wizard will launch. Input these values:

* Register an Existing SIP or IAX2 account
* Next
* SIP
* Next
* Alias: MyFirstAccount
* Hostname: <your asterisk server IP (use "ifconfig" on the server to check)>
* Username: 666
* Password: 123
* Next
* Apply

If you go in Edit -> Account, you should now see "MyFirstAccount" as "REGISTERED" (in green). If you see "Trying..." and run Asterisk on the same computer as SFLphone, you have to change the default port in the advanced settings (Edit->Accounts->Select your account->Edit->Advanced)

.. image:: /_static/sflphone7_2.png
   :scale: 85%



.. image:: /_static/sflphone8_0.png
   :scale: 85%



.. image:: /_static/sflphone9.png
   :scale: 85%
