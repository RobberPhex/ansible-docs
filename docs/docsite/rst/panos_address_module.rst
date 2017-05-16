.. _panos_address:


panos_address - Create address service object on PanOS devices
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create address service object of different types [IP Range, FQDN, or IP Netmask].


Requirements (on host that executes module)
-------------------------------------------

  * pan-python can be obtained from PyPi https://pypi.python.org/pypi/pan-python


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
                <tr><td>address<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>IP address with or without mask, range, or FQDN.</div>        </td></tr>
                <tr><td>address_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>Human readable name of the address.</div>        </td></tr>
                <tr><td>commit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Commit configuration to the Firewall if it is changed.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Description of the address object.</div>        </td></tr>
                <tr><td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>IP address (or hostname) of PAN-OS device being configured.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password credentials to use for authentication.</div>        </td></tr>
                <tr><td>tag<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Tag of the address object.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ip-nemask</td>
        <td><ul><li>ip-netmask</li><li>fqdn</li><li>ip-range</li></ul></td>
        <td><div>This is the type of the object created.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Username credentials to use for authentication.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create IP-Netmask Object
      panos_address:
        ip_address: "192.168.1.1"
        password: 'admin'
        address_name: 'google_dns'
        address: '8.8.8.8/32'
        description: 'Google DNS'
        tag: 'Outbound'
        commit: False
    
    - name: create IP-Range Object
      panos_address:
        ip_address: "192.168.1.1"
        password: 'admin'
        type: 'ip-range'
        address_name: 'apple-range'
        address: '17.0.0.0-17.255.255.255'
        commit: False
    
    - name: create FQDN Object
      panos_address:
        ip_address: "192.168.1.1"
        password: 'admin'
        type: 'fqdn'
        address_name: 'google.com'
        address: 'www.google.com'





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
