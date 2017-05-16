.. _cl_ports:


cl_ports - Configure Cumulus Switch port attributes (ports.conf)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Set the initial port attribute defined in the Cumulus Linux ports.conf, file. This module does not do any error checking at the moment. Be careful to not include ports that do not exist on the switch. Carefully read the original ports.conf file for any exceptions or limitations. For more details go the Configure Switch Port Attribute Documentation at http://docs.cumulusnetworks.com.




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
    <td>speed_10g<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of ports to run initial run at 10G.</div></td></tr>
            <tr>
    <td>speed_40g<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of ports to run initial run at 40G.</div></td></tr>
            <tr>
    <td>speed_40g_div_4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of 10G ports that will be ganged to form a 40G port.</div></td></tr>
            <tr>
    <td>speed_4_by_10g<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of 40G ports that will be unganged to run as 4 10G ports.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    Example playbook entries using the cl_ports module to manage the switch
    attributes defined in the ports.conf file on Cumulus Linux
    
    ## Unganged port config using simple args
       - name: configure ports.conf setup
         cl_ports: speed_4_by_10g="swp1, swp32" speed_40g="swp2-31"
         notify: restart switchd
    
    ## Unganged port configuration on certain ports using complex args
    
        - name: configure ports.conf setup
          cl_ports:
              speed_4_by_10g: ['swp1-3', 'swp6']
              speed_40g: ['swp4-5', 'swp7-32']
          notify: restart switchd
    

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
        <td> msg </td>
        <td> human-readable report of success or failure </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> interface bond0 config updated </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> whether the interface was changed </td>
        <td align=center> changed </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

