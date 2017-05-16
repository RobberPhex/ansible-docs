.. _wakeonlan:


wakeonlan - Send a magic Wake-on-LAN (WoL) broadcast packet
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``wakeonlan`` module sends magic Wake-on-LAN (WoL) broadcast packets.




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
                <tr><td>broadcast<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>255.255.255.255</td>
        <td></td>
        <td><div>Network broadcast address to use for broadcasting magic Wake-on-LAN packet.</div>        </td></tr>
                <tr><td>mac<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>MAC address to send Wake-on-LAN broadcast packet for.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>7</td>
        <td></td>
        <td><div>UDP port to use for magic Wake-on-LAN packet.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Send a magic Wake-on-LAN packet to 00:00:5E:00:53:66
      wakeonlan:
        mac: '00:00:5E:00:53:66'
        broadcast: 192.0.2.23
      delegate_to: localhost
    
    - wakeonlan:
        mac: 00:00:5E:00:53:66
        port: 9
      delegate_to: localhost


Notes
-----

.. note::
    - This module sends a magic packet, without knowing whether it worked
    - Only works if the target system was properly configured for Wake-on-LAN (in the BIOS and/or the OS)
    - Some BIOSes have a different (configurable) Wake-on-LAN boot order (i.e. PXE first) when turned off



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
