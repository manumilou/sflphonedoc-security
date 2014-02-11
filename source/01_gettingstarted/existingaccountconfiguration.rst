.. _existingaccountconfiguration:

Configuring an existing account
===============

The simplest way to configure SFLphone is to use the First Run wizard.

* In the Unity lens interface (top left dock icon or “windows” key), type “sflphone”
* After a few seconds, a wizard window should appear on the screen with a welcome message

.. image:: /_static/accountwizard.png
  :scale: 65%

* Press "continue"
* Select "Register an existing SIP or IAX2 account"

.. image:: /_static/accounttype.png
  :scale: 75%

* Select your protocol (if unsure, use SIP)

.. image:: /_static/voipprotocols.png
  :scale: 75%

*  You will now see several fields

.. image:: /_static/accountsettings.png
  :scale: 75%

::

 Alias: A name you will remember (Example: Workplace)
 Hostname: usually the server address, (Example: sip.sflphone.org)
 Username: Usually your phone extension (Example: 123), but may also be a name
 Password: Your account password (Warning: will be stored in plain text)
 Voicemail number (optional): Another username you can call to play your voicemail. Not every SIP account has one.
 Secure communications with ZRTP: Do not check (see security section)

* Press continue and “apply”

.. image:: /_static/accountregistration.png

* If you now select “Edit->Accounts”, your new account should appear in green
