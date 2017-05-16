.. _hpilo_facts:


hpilo_facts - Gather facts through an HP iLO interface
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module gathers facts for a specific system using its HP iLO interface. These facts include hardware and network related information useful for provisioning (e.g. macaddress, uuid).
* This module requires the hpilo python module.


Requirements (on host that executes module)
-------------------------------------------

  * hpilo


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
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The HP iLO hostname/address that is linked to the physical system.</div>        </td></tr>
                <tr><td>login<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Administrator</td>
        <td></td>
        <td><div>The login name to authenticate to the HP iLO interface.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>The password to authenticate to the HP iLO interface.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Task to gather facts from a HP iLO interface only if the system is an HP server
    - hpilo_facts:
        host: YOUR_ILO_ADDRESS
        login: YOUR_ILO_LOGIN
        password: YOUR_ILO_PASSWORD
      when: cmdb_hwmodel.startswith('HP ')
      delegate_to: localhost
    
    - fail:
        msg: 'CMDB serial ({{ cmdb_serialno }}) does not match hardware serial ({{ hw_system_serial }}) !'
      when: cmdb_serialno != hw_system_serial

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
        <td> hw_bios_version </td>
        <td> BIOS version </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> P68 </td>
    </tr>
            <tr>
        <td> hw_product_name </td>
        <td> Product name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> ProLiant DL360 G7 </td>
    </tr>
            <tr>
        <td> hw_bios_date </td>
        <td> BIOS date </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 05/05/2011 </td>
    </tr>
            <tr>
        <td> hw_ethX </td>
        <td> Interface information (for each interface) </td>
        <td align=center> always </td>
        <td align=center> dictionary of information (macaddress) </td>
        <td align=center> [{'macaddress': '00:11:22:33:44:55', 'macaddress_dash': '00-11-22-33-44-55'}] </td>
    </tr>
            <tr>
        <td> hw_system_serial </td>
        <td> System serial number </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> ABC12345D6 </td>
    </tr>
            <tr>
        <td> hw_eth_ilo </td>
        <td> Interface information (for the iLO network interface) </td>
        <td align=center> always </td>
        <td align=center> dictionary of information (macaddress) </td>
        <td align=center> [{'macaddress': '00:11:22:33:44:BA'}, {'macaddress_dash': '00-11-22-33-44-BA'}] </td>
    </tr>
            <tr>
        <td> hw_uuid </td>
        <td> Hardware UUID </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 123456ABC78901D2 </td>
    </tr>
            <tr>
        <td> hw_product_uuid </td>
        <td> Product UUID </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> ef50bac8-2845-40ff-81d9-675315501dac </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - This module ought to be run from a system that can access the HP iLO interface directly, either by using ``local_action`` or using ``delegate_to``.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
