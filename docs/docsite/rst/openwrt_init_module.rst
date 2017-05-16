.. _openwrt_init:


openwrt_init - Manage services on OpenWrt.
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Controls OpenWrt services on remote hosts.


Requirements (on host that executes module)
-------------------------------------------

  * An OpenWrt system


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
                <tr><td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the service should start on boot. <b>At least one of state and enabled are required.</b></div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the service.</div></br>
    <div style="font-size: small;">aliases: service<div>        </td></tr>
                <tr><td>pattern<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If the service does not respond to the 'running' command, name a substring to look for as would be found in the output of the <em>ps</em> command as a stand-in for a 'running' result.  If the string is found, the service will be assumed to be running.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>reloaded</li></ul></td>
        <td><div><code>started</code>/<code>stopped</code> are idempotent actions that will not run commands unless necessary. <code>restarted</code> will always bounce the service. <code>reloaded</code> will always reload.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example action to start service httpd, if not running
    - openwrt_init:
        state: started
        name: httpd
    
    # Example action to stop service cron, if running
    - openwrt_init:
        name: cron
        state: stopped
    
    # Example action to reload service httpd, in all cases
    - openwrt_init:
        name: httpd
        state: reloaded
    
    # Example action to enable service httpd
    - openwrt_init:
        name: httpd
        enabled: yes


Notes
-----

.. note::
    - One option other than name is required.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
