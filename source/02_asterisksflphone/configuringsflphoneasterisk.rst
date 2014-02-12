.. _configuringsflphoneasterisk:

Configuring SFLphone with Asterisk
==================================

Once this is done, execute ``sflphone-client-gnome``. A :ref:`configuration wizard <existingaccountconfiguration>` will launch if you started it for the first time. 

Select the following values:

* Account: ``Register an Existing SIP or IAX2 account``, then ``Next``
* VoIP Protocols: ``SIP``, then ``Next``

As for the SIP account settings, input these values:

.. Nomenclature-table::

======================= ======================
Settings                Values
======================= ======================
Alias                   My First Account
Hostname                <your asterisk server IP>
Username                666
Password                123
======================= ======================

.. note::

 You may run ``ifconfig`` to check your IP address.

Then ``Next`` and ``Apply``.

If you go in ``Edit > Account``, you should now see *MyFirstAccount* as **Registered** (in green). If you see a **Trying...** status and run **Asterisk** on the same computer as SFLphone, you have to change the default port in your account advanced settings (``Edit > Accounts > Select your account > Edit > Advanced``).

.. figure:: /_static/sflphone7_2.png
    :scale: 85%
    :align: center
    :alt: Account list window

    Account list window, showing the accounts registration status.


.. figure:: /_static/sflphone8_0.png
    :scale: 85%
    :align: center
    :alt: Account advanced configuration

    The account's advanced settings allows to configure the network interface, port range and registration expiration time.


.. figure:: /_static/sflphone9.png
   :scale: 85%
   :align: center
   :alt: Test call
