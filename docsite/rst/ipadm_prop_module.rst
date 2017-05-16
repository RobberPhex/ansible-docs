.. _ipadm_prop:


ipadm_prop - Manage protocol properties on Solaris/illumos systems.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Modify protocol properties on Solaris/illumos systems.




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
    <td>property<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the name of property we want to manage.</div></td></tr>
            <tr>
    <td>protocol<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the procotol for which we want to manage properties.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>reset</li></ul></td>
        <td><div>Set or reset the property value.</div></td></tr>
            <tr>
    <td>temporary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Specifies that the property value is temporary. Temporary property values do not persist across reboots.</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the value we want to set for the property.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set TCP receive buffer size
    ipadm_prop: protocol=tcp property=recv_buf value=65536
    
    # Reset UDP send buffer size to the default value
    ipadm_prop: protocol=udp property=send_buf state=reset

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
        <td> protocol </td>
        <td> property's protocol </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> TCP </td>
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
        <td> name of the property </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> recv_maxbuf </td>
    </tr>
            <tr>
        <td> temporary </td>
        <td> property's persistence </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> value </td>
        <td> value of the property </td>
        <td align=center> always </td>
        <td align=center> int/string (depends on property) </td>
        <td align=center> 1024/never </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

