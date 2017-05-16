.. _ipadm_ifprop:


ipadm_ifprop - Manage IP interface properties on Solaris/illumos systems.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Modify IP interface properties on Solaris/illumos systems.




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
                <tr><td>interface<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the IP interface we want to manage.</div></br>
    <div style="font-size: small;">aliases: nic<div>        </td></tr>
                <tr><td>property<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the name of the property we want to manage.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>protocol<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the procotol for which we want to manage properties.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>reset</li></ul></td>
        <td><div>Set or reset the property value.</div>        </td></tr>
                <tr><td>temporary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies that the property value is temporary. Temporary property values do not persist across reboots.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the value we want to set for the property.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    name: Allow forwarding of IPv4 packets on network interface e1000g0
    ipadm_ifprop: protocol=ipv4 property=forwarding value=on interface=e1000g0
    
    name: Temporarily reset IPv4 forwarding property on network interface e1000g0
    ipadm_ifprop: protocol=ipv4 interface=e1000g0  temporary=true property=forwarding state=reset
    
    name: Configure IPv6 metric on network interface e1000g0
    ipadm_ifprop: protocol=ipv6 nic=e1000g0 name=metric value=100
    
    name: Set IPv6 MTU on network interface bge0
    ipadm_ifprop: interface=bge0 name=mtu value=1280 protocol=ipv6

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
        <td> interface </td>
        <td> interface name we want to set property on </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center> e1000g0 </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state of the target </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> property </td>
        <td> property's name </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center> mtu </td>
    </tr>
            <tr>
        <td> protocol </td>
        <td> property's protocol </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center> ipv4 </td>
    </tr>
            <tr>
        <td> value </td>
        <td> property's value </td>
        <td align=center> when value is provided </td>
        <td align=center> str </td>
        <td align=center> 1280 </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
