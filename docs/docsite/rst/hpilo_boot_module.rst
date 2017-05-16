.. _hpilo_boot:


hpilo_boot - Boot system using specific media through HP iLO interface
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module boots a system through its HP iLO interface. The boot media can be one of: cdrom, floppy, hdd, network or usb.
* This module requires the hpilo python module.


Requirements (on host that executes module)
-------------------------------------------

  * hpilo


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
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to force a reboot (even when the system is already booted).</div><div>As a safeguard, without force, hpilo_boot will refuse to reboot a server that is already running.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The HP iLO hostname/address that is linked to the physical system.</div>        </td></tr>
                <tr><td>image<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The URL of a cdrom, floppy or usb boot media image. protocol://username:password@hostname:port/filename</div><div>protocol is either 'http' or 'https'</div><div>username:password is optional</div><div>port is optional</div>        </td></tr>
                <tr><td>login<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Administrator</td>
        <td></td>
        <td><div>The login name to authenticate to the HP iLO interface.</div>        </td></tr>
                <tr><td>media<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>network</td>
        <td><ul><li>cdrom</li><li>floppy</li><li>hdd</li><li>network</li><li>normal</li><li>usb</li></ul></td>
        <td><div>The boot media to boot the system from</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>The password to authenticate to the HP iLO interface.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>boot_once</td>
        <td><ul><li>boot_always</li><li>boot_once</li><li>connect</li><li>disconnect</li><li>no_boot</li><li>poweroff</li></ul></td>
        <td><div>The state of the boot media.</div><div>no_boot: Do not boot from the device</div><div>boot_once: Boot from the device once and then notthereafter</div><div>boot_always: Boot from the device each time the serveris rebooted</div><div>connect: Connect the virtual media device and set to boot_always</div><div>disconnect: Disconnects the virtual media device and set to no_boot</div><div>poweroff: Power off the server</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Task to boot a system using an ISO from an HP iLO interface only if the system is an HP server
      hpilo_boot:
        host: YOUR_ILO_ADDRESS
        login: YOUR_ILO_LOGIN
        password: YOUR_ILO_PASSWORD
        media: cdrom
        image: http://some-web-server/iso/boot.iso
      when: cmdb_hwmodel.startswith('HP ')
      delegate_to: localhost
    
    - name: Power off a server
      hpilo_boot:
        host: YOUR_ILO_HOST
        login: YOUR_ILO_LOGIN
        password: YOUR_ILO_PASSWORD
        state: poweroff
      delegate_to: localhost


Notes
-----

.. note::
    - To use a USB key image you need to specify floppy as boot media.
    - This module ought to be run from a system that can access the HP iLO interface directly, either by using ``local_action`` or using ``delegate_to``.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
