.. _ipadm_addrprop:


ipadm_addrprop - Manage IP address properties on Solaris/illumos systems.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Modify IP address properties on Solaris/illumos systems.




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
                <tr><td>addrobj<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the address object we want to manage.</div></br>
    <div style="font-size: small;">aliases: nic, interface<div>        </td></tr>
                <tr><td>property<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the name of the address property we want to manage.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>reset</li></ul></td>
        <td><div>Set or reset the property value.</div>        </td></tr>
                <tr><td>temporary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies that the address property value is temporary. Temporary values do not persist across reboots.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the value we want to set for the address property.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    name: Mark address on addrobj as deprecated
    ipadm_addrprop: property=deprecated value=on addrobj=e1000g0/v6
    
    name: Set network prefix length for addrobj
    ipadm_addrprop: addrobj=bge0/v4 name=prefixlen value=26

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
        <td> property </td>
        <td> property name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> deprecated </td>
    </tr>
            <tr>
        <td> temporary </td>
        <td> specifies if operation will persist across reboots </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> value </td>
        <td> property value </td>
        <td align=center> when value is provided </td>
        <td align=center> string </td>
        <td align=center> 26 </td>
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
