.. _exo_dns_record:


exo_dns_record - Manages DNS records on Exoscale DNS.
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update and delete records.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6


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
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API key of the Exoscale DNS API.</div></td></tr>
            <tr>
    <td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td><ul></ul></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div></td></tr>
            <tr>
    <td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Secret key of the Exoscale DNS API.</div></td></tr>
            <tr>
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>HTTP timeout to Exoscale DNS API.</div></td></tr>
            <tr>
    <td>content<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Content of the record.</div><div>Required if <code>state=present</code> or <code>name=""</code></div></br>
        <div style="font-size: small;">aliases: value, address<div></td></tr>
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Domain the record is related to.</div></td></tr>
            <tr>
    <td>multiple<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether there are more than one records with similar <code>name</code>.</div><div>Only allowed with <code>record_type=A</code>.</div><div><code>content</code> will not be updated as it is used as key to find the record.</div></br>
        <div style="font-size: small;">aliases: priority<div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the record.</div></td></tr>
            <tr>
    <td>prio<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Priority of the record.</div></br>
        <div style="font-size: small;">aliases: priority<div></td></tr>
            <tr>
    <td>record_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>A</td>
        <td><ul><li>A</li><li>ALIAS</li><li>CNAME</li><li>MX</li><li>SPF</li><li>URL</li><li>TXT</li><li>NS</li><li>SRV</li><li>NAPTR</li><li>PTR</li><li>AAAA</li><li>SSHFP</li><li>HINFO</li><li>POOL</li></ul></td>
        <td><div>Type of the record.</div></br>
        <div style="font-size: small;">aliases: rtype, type<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the record.</div></td></tr>
            <tr>
    <td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3600</td>
        <td><ul></ul></td>
        <td><div>TTL of the record in seconds.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Validate SSL certs of the Exoscale DNS API.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create or update an A record.
    - local_action:
        module: exo_dns_record
        name: web-vm-1
        domain: example.com
        content: 1.2.3.4
    
    # Update an existing A record with a new IP.
    - local_action:
        module: exo_dns_record
        name: web-vm-1
        domain: example.com
        content: 1.2.3.5
    
    # Create another A record with same name.
    - local_action:
        module: exo_dns_record
        name: web-vm-1
        domain: example.com
        content: 1.2.3.6
        multiple: yes
    
    # Create or update a CNAME record.
    - local_action:
        module: exo_dns_record
        name: www
        domain: example.com
        record_type: CNAME
        content: web-vm-1
    
    # Create or update a MX record.
    - local_action:
        module: exo_dns_record
        domain: example.com
        record_type: MX
        content: mx1.example.com
        prio: 10
    
    # delete a MX record.
    - local_action:
        module: exo_dns_record
        domain: example.com
        record_type: MX
        content: mx1.example.com
        state: absent
    
    # Remove a record.
    - local_action:
        module: exo_dns_record
        name: www
        domain: example.com
        state: absent

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
        <td> exo_dns_record </td>
        <td> API record results </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> domain </td>
        <td> Name of the domain </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example.com </td>
        </tr>
                <tr>
        <td> name </td>
        <td> name of the record </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> www </td>
        </tr>
                <tr>
        <td> prio </td>
        <td> Priority of the record </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
        </tr>
                <tr>
        <td> parent_id </td>
        <td> ID of the parent </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> None </td>
        </tr>
                <tr>
        <td> system_record </td>
        <td> Whether the record is a system record or not </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> created_at </td>
        <td> When the record was created </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2016-08-12T15:24:23.989Z </td>
        </tr>
                <tr>
        <td> updated_at </td>
        <td> When the record was updated </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2016-08-12T15:24:23.989Z </td>
        </tr>
                <tr>
        <td> id </td>
        <td> ID of the record </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 254324 </td>
        </tr>
                <tr>
        <td> content </td>
        <td> value of the record </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.2.3.4 </td>
        </tr>
                <tr>
        <td> record_type </td>
        <td> Priority of the record </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> A </td>
        </tr>
                <tr>
        <td> ttl </td>
        <td> Time to live of the record </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 3600 </td>
        </tr>
                <tr>
        <td> domain_id </td>
        <td> ID of the domain </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 254324 </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note:: As Exoscale DNS uses the same API key and secret for all services, we reuse the config used for Exscale Compute based on CloudStack. The config is read from several locations, in the following order. The ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` environment variables. A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, A ``cloudstack.ini`` file in the current working directory. A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``.
.. note:: This module does not support multiple A records and will complain properly if you try.
.. note:: More information Exoscale DNS can be found on https://community.exoscale.ch/documentation/dns/.
.. note:: This module supports check mode and diff.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

