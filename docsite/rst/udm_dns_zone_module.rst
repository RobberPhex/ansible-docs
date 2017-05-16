.. _udm_dns_zone:


udm_dns_zone - Manage dns zones on a univention corporate server
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows to manage dns zones on a univention corporate server (UCS). It uses the python API of the UCS to create a new object or edit it.


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
    <td>contact<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Contact person in the SOA record.</div></td></tr>
            <tr>
    <td>expire<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>604800</td>
        <td><ul></ul></td>
        <td><div>Specifies the upper limit on the time interval that can elapse before the zone is no longer authoritative.</div></td></tr>
            <tr>
    <td>interfaces<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of interface IP addresses, on which the server should response this zone. Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>mx<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of MX servers. (Must declared as A or AAAA records).</div></td></tr>
            <tr>
    <td>nameserver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of appropriate name servers. Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>refresh<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3600</td>
        <td><ul></ul></td>
        <td><div>Interval before the zone should be refreshed.</div></td></tr>
            <tr>
    <td>retry<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1800</td>
        <td><ul></ul></td>
        <td><div>Interval that should elapse before a failed refresh should be retried.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the dns zone is present or not.</div></td></tr>
            <tr>
    <td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>Minimum TTL field that should be exported with any RR from this zone.</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>forward_zone</li><li>reverse_zone</li></ul></td>
        <td><div>Define if the zone is a forward or reverse DNS zone.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>DNS zone name, e.g. <code>example.com</code>.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a DNS zone on a UCS
    - udm_dns_zone: zone=example.com
                    type=forward_zone
                    nameserver=['ucs.example.com']
                    interfaces=['192.0.2.1']




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

