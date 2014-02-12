.. _installingsflphone:

Install SFLphone
================

First, you need to add the official SFLphone PPA (Personal Package Archive). This allows us to push new versions for older distributions.

.. note::

 This step is not mandatory as Ubuntu provides SFLphone packages in its *universe* repository.

Solution 1: Software Center
--------------------------

* Open Software Center (in Unity, press the ``Windows`` key and type `software center`)

.. image:: /_static/softwarecenter0.png
  :scale: 75%
  :align: center


* In ``Edit > Software`` sources, select the *Other software* tab
* Click ``add`` and enter `ppa:savoirfairelinux`
* Click ``close``
* Click the little arrow next to *All Software* and select sflphone
* Select **GNOME client for SFLphone** and click ``Install``


Solution 2: Command-line
-----------------------

Add the repository to your software sources:

::

  sudo add-apt-repository ppa:savoirfairelinux

Now, update the package list:

::

  sudo apt-get update

You can now install the latest SFLphone version:

::

 sudo apt-get install sflphone-client-gnome 


Solution 3: Building from sources (not recommended)
-----------

Please refer to the instructions at https://projects.savoirfairelinux.com/projects/sflphone/wiki/How_to_build to build SFLphone from source.




