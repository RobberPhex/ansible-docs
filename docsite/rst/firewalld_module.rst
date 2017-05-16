.. _firewalld:


firewalld - Manage arbitrary ports/services with firewalld
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows for addition or deletion of services and ports either tcp or udp in either running or permanent firewalld rules.


Requirements (on host that executes module)
-------------------------------------------

  * firewalld >= 0.2.11


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
            <tr>
    <td>immediate<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Should this configuration be applied immediately, if set as permanent</div></td></tr>
            <tr>
    <td>interface<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The interface you would like to add/remove to/from a zone in firewalld</div></td></tr>
            <tr>
    <td>masquerade<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The masquerade setting you would like to enable/disable to/from zones within firewalld</div></td></tr>
            <tr>
    <td>permanent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Should this configuration be in the running firewalld configuration or persist across reboots.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of a port or port range to add/remove to/from firewalld. Must be in the form PORT/PROTOCOL or PORT-PORT/PROTOCOL for port ranges.</div></td></tr>
            <tr>
    <td>rich_rule<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Rich rule to add/remove to/from firewalld.</div></td></tr>
            <tr>
    <td>service<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of a service to add/remove to/from firewalld - service must be listed in /etc/services.</div></td></tr>
            <tr>
    <td>source<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The source/network you would like to add/remove to/from firewalld</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>Should this port accept(enabled) or reject(disabled) connections.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The amount of time the rule should be in effect for when non-permanent.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>system-default(public)</td>
        <td><ul><li>work</li><li>drop</li><li>internal</li><li>external</li><li>trusted</li><li>home</li><li>dmz</li><li>public</li><li>block</li></ul></td>
        <td><div>The firewalld zone to add/remove to/from (NOTE: default zone can be configured per system but "public" is default from upstream. Available choices can be extended based on per-system configs, listed here are "out of the box" defaults).</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - firewalld: service=https permanent=true state=enabled
    - firewalld: port=8081/tcp permanent=true state=disabled
    - firewalld: port=161-162/udp permanent=true state=enabled
    - firewalld: zone=dmz service=http permanent=true state=enabled
    - firewalld: rich_rule='rule service name="ftp" audit limit value="1/m" accept' permanent=true state=enabled
    - firewalld: source='192.0.2.0/24' zone=internal state=enabled
    - firewalld: zone=trusted interface=eth2 permanent=true state=enabled
    - firewalld: masquerade=yes state=enabled permanent=true zone=dmz


Notes
-----

.. note:: Not tested on any Debian based system.
.. note:: Requires the python2 bindings of firewalld, which may not be installed by default if the distribution switched to python 3


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

