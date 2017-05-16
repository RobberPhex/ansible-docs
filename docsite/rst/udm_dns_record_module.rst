.. _udm_dns_record:


udm_dns_record - Manage dns entries on a univention corporate server
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows to manage dns records on a univention corporate server (UCS). It uses the python API of the UCS to create a new object or edit it.


Requirements (on host that executes module)
-------------------------------------------

  * Python >= 2.6


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
    <td>data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Additional data for this record, e.g. ['a': '192.0.2.1']. Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the record, this is also the DNS record. E.g. www for www.example.com.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the dns record is present or not.</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>host_record</li><li>alias</li><li>ptr_record</li><li>srv_record</li><li>txt_record</li></ul></td>
        <td><div>Define the record type. <code>host_record</code> is a A or AAAA record, <code>alias</code> is a CNAME, <code>ptr_record</code> is a PTR record, <code>srv_record</code> is a SRV record and <code>txt_record</code> is a TXT record.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Corresponding DNS zone for this record, e.g. example.com.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a DNS record on a UCS
    - udm_dns_zone: name=www
                    zone=example.com
                    type=host_record
                    data=['a': '192.0.2.1']




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

