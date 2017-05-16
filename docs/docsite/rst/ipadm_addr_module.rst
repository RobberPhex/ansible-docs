.. _ipadm_addr:


ipadm_addr - Manage IP addresses on an interface on Solaris/illumos systems
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create/delete static/dynamic IP addresses on network interfaces on Solaris/illumos systems.
* Up/down static/dynamic IP addresses on network interfaces on Solaris/illumos systems.
* Manage IPv6 link-local addresses on network interfaces on Solaris/illumos systems.




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
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifiies an IP address to configure in CIDR notation.</div></br>
    <div style="font-size: small;">aliases: addr<div>        </td></tr>
                <tr><td>addrobj<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies an unique IP address on the system.</div>        </td></tr>
                <tr><td>addrtype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>static</td>
        <td><ul><li>static</li><li>dhcp</li><li>addrconf</li></ul></td>
        <td><div>Specifiies a type of IP address to configure.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li><li>up</li><li>down</li><li>enabled</li><li>disabled</li><li>refreshed</li></ul></td>
        <td><div>Create/delete/enable/disable an IP address on the network interface.</div>        </td></tr>
                <tr><td>temporary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies that the configured IP address is temporary. Temporary IP addresses do not persist across reboots.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>60</td>
        <td></td>
        <td><div>Specifies the time in seconds we wait for obtaining address via DHCP.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    name: Configure IP address 10.0.0.1 on e1000g0
    ipadm_addr: addr=10.0.0.1/32 addrobj=e1000g0/v4 state=present
    
    name: Delete addrobj
    ipadm_addr: addrobj=e1000g0/v4 state=absent
    
    name: Configure link-local IPv6 address
    ipadm_addr: addtype=addrconf addrobj=vnic0/v6
    
    name: Configure address via DHCP and wait 180 seconds for address obtaining
    ipadm_addr: addrobj=vnic0/dhcp addrtype=dhcp wait=180

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
        <td> addrtype </td>
        <td> address type </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> static </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state of the target </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> temporary </td>
        <td> specifies if operation will persist across reboots </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> address </td>
        <td> IP address </td>
        <td align=center> only if addrtype is 'static' </td>
        <td align=center> string </td>
        <td align=center> 1.3.3.7/32 </td>
    </tr>
            <tr>
        <td> wait </td>
        <td> time we wait for DHCP </td>
        <td align=center> only if addrtype is 'dhcp' </td>
        <td align=center> string </td>
        <td align=center> 10 </td>
    </tr>
            <tr>
        <td> addrobj </td>
        <td> address object name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> bge0/v4 </td>
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
