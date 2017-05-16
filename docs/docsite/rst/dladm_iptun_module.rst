.. _dladm_iptun:


dladm_iptun - Manage IP tunnel interfaces on Solaris/illumos systems.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage IP tunnel interfaces on Solaris/illumos systems.




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
                <tr><td>local_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Literat IP address or hostname corresponding to the tunnel source.</div></br>
    <div style="font-size: small;">aliases: local<div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>IP tunnel interface name.</div></br>
    <div style="font-size: small;">aliases: tunnel, link<div>        </td></tr>
                <tr><td>remote_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Literal IP address or hostname corresponding to the tunnel destination.</div></br>
    <div style="font-size: small;">aliases: remote<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or delete Solaris/illumos VNIC.</div>        </td></tr>
                <tr><td>temporary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies that the IP tunnel interface is temporary. Temporary IP tunnel interfaces do not persist across reboots.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ipv4</td>
        <td><ul><li>ipv4</li><li>ipv6</li><li>6to4</li></ul></td>
        <td><div>Specifies the type of tunnel to be created.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    name: Create IPv4 tunnel interface 'iptun0'
    dladm_iptun: name=iptun0 local_address=192.0.2.23 remote_address=203.0.113.10 state=present
    
    name: Change IPv4 tunnel remote address
    dladm_iptun: name=iptun0 type=ipv4 local_address=192.0.2.23 remote_address=203.0.113.11
    
    name: Create IPv6 tunnel interface 'tun0'
    dladm_iptun: name=tun0 type=ipv6 local_address=192.0.2.23 remote_address=203.0.113.42
    
    name: Remove 'iptun0' tunnel interface
    dladm_iptun: name=iptun0 state=absent

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
        <td> name </td>
        <td> tunnel interface name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> iptun0 </td>
    </tr>
            <tr>
        <td> local_address </td>
        <td> local IP address </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 1.1.1.1/32 </td>
    </tr>
            <tr>
        <td> type </td>
        <td> tunnel type </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> ipv4 </td>
    </tr>
            <tr>
        <td> remote_address </td>
        <td> remote IP address </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 2.2.2.2/32 </td>
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
