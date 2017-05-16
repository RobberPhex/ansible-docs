.. _dladm_linkprop:


dladm_linkprop - Manage link properties on Solaris/illumos systems.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Set / reset link properties on Solaris/illumos systems.




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
                <tr><td>link<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Link interface name.</div></br>
    <div style="font-size: small;">aliases: nic, interface<div>        </td></tr>
                <tr><td>property<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the name of the property we want to manage.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>reset</li></ul></td>
        <td><div>Set or reset the property value.</div>        </td></tr>
                <tr><td>temporary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies that lin property configuration is temporary. Temporary link property configuration does not persist across reboots.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the value we want to set for the link property.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    name: Set 'maxbw' to 100M on e1000g1
    dladm_linkprop: name=e1000g1 property=maxbw value=100M state=present
    
    name: Set 'mtu' to 9000 on e1000g1
    dladm_linkprop: name=e1000g1 property=mtu value=9000
    
    name: Reset 'mtu' property on e1000g1
    dladm_linkprop: name=e1000g1 property=mtu state=reset

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
        <td> temporary </td>
        <td> specifies if operation will persist across reboots </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
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
        <td align=center> mtu </td>
    </tr>
            <tr>
        <td> link </td>
        <td> link name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> e100g0 </td>
    </tr>
            <tr>
        <td> value </td>
        <td> property value </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 9000 </td>
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
