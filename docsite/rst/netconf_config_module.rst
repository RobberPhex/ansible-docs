.. _netconf_config:


netconf_config - netconf device configuration
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Netconf is a network management protocol developed and standardized by the IETF. It is documented in RFC 6241.
This module allows the user to send a configuration XML file to a netconf device, and detects if there was a configuration change.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * ncclient


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
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the hostname or ip address of the netconf device</div></td></tr>
            <tr>
    <td>hostkey_verify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>if true, the ssh host key of the device must match a ssh key present on the host</div><div>if false, the ssh host key of the device is not checked</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>password of the user to authenticate with</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>830</td>
        <td><ul></ul></td>
        <td><div>the netconf port</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the username to authenticate with</div></td></tr>
            <tr>
    <td>xml<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the XML content to send to the device</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: set ntp server in the device
      netconf_config:
        host: 10.0.0.1
        username: admin
        password: admin
        xml: |
            <config xmlns:xc="urn:ietf:params:xml:ns:netconf:base:1.0">
                <system xmlns="urn:ietf:params:xml:ns:yang:ietf-system">
                    <ntp>
                        <enabled>true</enabled>
                        <server>
                            <name>ntp1</name>
                            <udp><address>127.0.0.1</address></udp>
                        </server>
                    </ntp>
                </system>
            </config>
    
    - name: wipe ntp configuration
      netconf_config:
        host: 10.0.0.1
        username: admin
        password: admin
        xml: |
            <config xmlns:xc="urn:ietf:params:xml:ns:netconf:base:1.0">
                <system xmlns="urn:ietf:params:xml:ns:yang:ietf-system">
                    <ntp>
                        <enabled>false</enabled>
                        <server operation="remove">
                            <name>ntp1</name>
                        </server>
                    </ntp>
                </system>
            </config>
    

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> server_capabilities </td>
        <td> list of capabilities of the server </td>
        <td align=center> success </td>
        <td align=center> list of strings </td>
        <td align=center> ['urn:ietf:params:netconf:base:1.1', 'urn:ietf:params:netconf:capability:confirmed-commit:1.0', 'urn:ietf:params:netconf:capability:candidate:1.0'] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: This module supports devices with and without the the candidate and confirmed-commit capabilities. It always use the safer feature.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

