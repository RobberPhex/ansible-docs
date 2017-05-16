.. _cl_interface_policy:


cl_interface_policy - Configure interface enforcement policy on Cumulus Linux
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module affects the configuration files located in the interfaces folder defined by ifupdown2. Interfaces port and port ranges listed in the "allowed" parameter define what interfaces will be available on the switch. If the user runs this module and has an interface configured on the switch, but not found in the "allowed" list, this interface will be unconfigured. By default this is `/etc/network/interface.d` For more details go the Configuring Interfaces at http://docs.cumulusnetworks.com




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
    <td>allowed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>list of ports to run initial run at 10G</div></td></tr>
            <tr>
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/network/interfaces.d/</td>
        <td><ul></ul></td>
        <td><div>folder to store interface files.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    Example playbook entries using the cl_interface_policy module.
    
        - name: shows types of interface ranges supported
          cl_interface_policy:
              allowed: "lo eth0 swp1-9, swp11, swp12-13s0, swp12-30s1, swp12-30s2, bond0-12"
    

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

Notes
-----

.. note:: lo must be included in the allowed list.
.. note:: eth0 must be in allowed list if out of band management is done


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

