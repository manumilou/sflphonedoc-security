.. _existingaccountconfiguration:

Configuring an existing account
===============

The simplest way to configure SFLphone is to use the *First Run* wizard.

* In the Unity lens interface (top left dock icon or ``Windows`` key), type `sflphone`
* After a few seconds, a wizard window should appear on the screen with a welcome message
* Press ``Continue`` to start the wizard

.. note::

 You can always return to the installation wizard in SFLphone by clicking the menu ``Call > Configuration Assistant``

.. figure:: /_static/accountwizard.png
  :scale: 65%
  :align: center

  Account configuration wizard: first step.


Account
~~~~~~~

Select ``Register an existing SIP or IAX2 account``

.. figure:: /_static/accounttype.png
  :scale: 75%
  :align: center

  Account configuration wizard: Account window.


VoIP Protocols
~~~~~~~~~~~~~

You can select here the communication protocol to use to make calls (if unsure, use SIP).

.. figure:: /_static/voipprotocols.png
  :scale: 75%
  :align: center

  Account configuration wizard: VoIP Protocols window.


Account settings
~~~~~~~~~~~~~~~~~~

This step allows you to set up your account, by specifying the hostname, username, password, ...


.. figure:: /_static/accountsettings.png
  :scale: 75%
  :align: center

  Account configuration wizard: Account settings.


Here are the details of each settings: 

.. _Nomenclature-table:

==================================  ============
Fields                              Description
==================================  ============
Alias                               A name you will remember (Example: Workplace)
Hostname                            Usually the server address, (Example: sip.sflphone.org)
Username                            Usually your phone extension (Example: 123), but may also be a name
Password                            Your account password (Warning: will be stored in plain text)
Voicemail number (optional)         Another username you can call to play your voicemail. Not every SIP account has one
Secure communications with ZRTP     Do not check (see security section)
==================================  ============


Press ``Continue`` and ``Apply`` when you are ready to register your account.

.. figure:: /_static/accountregistration.png
  :scale: 75%
  :align: center

  Account configuration wizard: Review


Account registration
~~~~~~~~~~~~~~~~~~~

The last panel displays an overview of your account settings. You may now click on ``Close``, as the installation wizard is finishow now. 

If you now select ``Edit > Accounts``, your new account should be registered, and appear in green.
