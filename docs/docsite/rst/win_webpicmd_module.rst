.. _win_webpicmd:


win_webpicmd - Installs packages using Web Platform Installer command-line
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Installs packages using Web Platform Installer command-line (http://www.iis.net/learn/install/web-platform-installer/web-platform-installer-v4-command-line-webpicmdexe-rtw-release).
* Must be installed and present in PATH (see win_chocolatey module; 'webpicmd' is the package name, and you must install 'lessmsi' first too)
* Install IIS first (see win_feature module)




Options
-------

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the package to be installed</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Install URLRewrite2.
      win_webpicmd:
        name: URLRewrite2


Notes
-----

.. note::
    - accepts EULAs and suppresses reboot - you will need to check manage reboots yourself (see win_reboot module)



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
