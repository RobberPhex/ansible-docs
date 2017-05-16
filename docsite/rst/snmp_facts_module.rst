.. _snmp_facts:


snmp_facts - Retrieve facts for a device using SNMP.
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Retrieve facts for a device using SNMP, the facts will be inserted to the ansible_facts key.


Requirements (on host that executes module)
-------------------------------------------

  * pysnmp


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
    <td>authkey<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Authentication key, required if version is v3</div></td></tr>
            <tr>
    <td>community<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The SNMP community string, required if version is v2/v2c</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set to target snmp server (normally {{inventory_hostname}})</div></td></tr>
            <tr>
    <td>integrity<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>md5</li><li>sha</li></ul></td>
        <td><div>Hashing algoritm, required if version is v3</div></td></tr>
            <tr>
    <td>level<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>authPriv</li><li>authNoPriv</li></ul></td>
        <td><div>Authentication level, required if version is v3</div></td></tr>
            <tr>
    <td>privacy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>des</li><li>aes</li></ul></td>
        <td><div>Encryption algoritm, required if level is authPriv</div></td></tr>
            <tr>
    <td>privkey<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Encryption key, required if version is authPriv</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username for SNMPv3, required if version is v3</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>v2</li><li>v2c</li><li>v3</li></ul></td>
        <td><div>SNMP Version to use, v2/v2c or v3</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Gather facts with SNMP version 2
    - snmp_facts: host={{ inventory_hostname }} version=2c community=public
      connection: local
    
    # Gather facts using SNMP version 3
    - snmp_facts:
        host={{ inventory_hostname }}
        version=v3
        level=authPriv
        integrity=sha
        privacy=aes
        username=snmp-user
        authkey=abc12345
        privkey=def6789
      delegate_to: localhost




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

