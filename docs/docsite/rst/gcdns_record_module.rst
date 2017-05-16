.. _gcdns_record:


gcdns_record - Creates or removes resource records in Google Cloud DNS
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates or removes resource records in Google Cloud DNS.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud >= 0.19.0


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
                <tr><td>credentials_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to the JSON file associated with the service account email.</div>        </td></tr>
                <tr><td>overwrite<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Whether an attempt to overwrite an existing record should succeed or fail. The behavior of this option depends on <em>state</em>.</div><div>If <em>state</em> is <code>present</code> and <em>overwrite</em> is <code>True</code>, this module will replace an existing resource record of the same name with the provided <em>record_data</em>. If <em>state</em> is <code>present</code> and <em>overwrite</em> is <code>False</code>, this module will fail if there is an existing resource record with the same name and type, but different resource data.</div><div>If <em>state</em> is <code>absent</code> and <em>overwrite</em> is <code>True</code>, this module will remove the given resource record unconditionally. If <em>state</em> is <code>absent</code> and <em>overwrite</em> is <code>False</code>, this module will fail if the provided record_data do not match exactly with the existing resource record's record_data.</div>        </td></tr>
                <tr><td>pem_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to the PEM file associated with the service account email.</div><div>This option is deprecated and may be removed in a future release. Use <em>credentials_file</em> instead.</div>        </td></tr>
                <tr><td>project_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The Google Cloud Platform project ID to use.</div>        </td></tr>
                <tr><td>record<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The fully-qualified domain name of the resource record.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>record_data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The record_data to use for the resource record.</div><div><em>record_data</em> must be specified if <em>state</em> is <code>present</code> or <em>overwrite</em> is <code>True</code>, or the module will fail.</div><div>Valid record_data vary based on the record's <em>type</em>. In addition, resource records that contain a DNS domain name in the value field (e.g., CNAME, PTR, SRV, .etc) MUST include a trailing dot in the value.</div><div>Individual string record_data for TXT records must be enclosed in double quotes.</div><div>For resource records that have the same name but different record_data (e.g., multiple A records), they must be defined as multiple list entries in a single record.</div></br>
    <div style="font-size: small;">aliases: value<div>        </td></tr>
                <tr><td>service_account_email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The e-mail address for a service account with access to Google Cloud DNS.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the given resource record should or should not be present.</div>        </td></tr>
                <tr><td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>The amount of time in seconds that a resource record will remain cached by a caching resolver.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>A</li><li>AAAA</li><li>CNAME</li><li>SRV</li><li>TXT</li><li>SOA</li><li>NS</li><li>MX</li><li>SPF</li><li>PTR</li></ul></td>
        <td><div>The type of resource record to add.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The DNS domain name of the zone (e.g., example.com).</div><div>One of either <em>zone</em> or <em>zone_id</em> must be specified as an option, or the module will fail.</div><div>If both <em>zone</em> and <em>zone_id</em> are specifed, <em>zone_id</em> will be used.</div>        </td></tr>
                <tr><td>zone_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The Google Cloud ID of the zone (e.g., example-com).</div><div>One of either <em>zone</em> or <em>zone_id</em> must be specified as an option, or the module will fail.</div><div>These usually take the form of domain names with the dots replaced with dashes. A zone ID will never have any dots in it.</div><div><em>zone_id</em> can be faster than <em>zone</em> in projects with a large number of zones.</div><div>If both <em>zone</em> and <em>zone_id</em> are specifed, <em>zone_id</em> will be used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create an A record.
    - gcdns_record:
        record: 'www1.example.com'
        zone: 'example.com'
        type: A
        value: '1.2.3.4'
    
    # Update an existing record.
    - gcdns_record:
        record: 'www1.example.com'
        zone: 'example.com'
        type: A
        overwrite: true
        value: '5.6.7.8'
    
    # Remove an A record.
    - gcdns_record:
        record: 'www1.example.com'
        zone_id: 'example-com'
        state: absent
        type: A
        value: '5.6.7.8'
    
    # Create a CNAME record.
    - gcdns_record:
        record: 'www.example.com'
        zone_id: 'example-com'
        type: CNAME
        value: 'www.example.com.'    # Note the trailing dot
    
    # Create an MX record with a custom TTL.
    - gcdns_record:
        record: 'example.com'
        zone: 'example.com'
        type: MX
        ttl: 3600
        value: '10 mail.example.com.'    # Note the trailing dot
    
    # Create multiple A records with the same name.
    - gcdns_record:
        record: 'api.example.com'
        zone_id: 'example-com'
        type: A
        record_data:
          - '192.0.2.23'
          - '10.4.5.6'
          - '198.51.100.5'
          - '203.0.113.10'
    
    # Change the value of an existing record with multiple record_data.
    - gcdns_record:
        record: 'api.example.com'
        zone: 'example.com'
        type: A
        overwrite: true
        record_data:           # WARNING: All values in a record will be replaced
          - '192.0.2.23'
          - '192.0.2.42'    # The changed record
          - '198.51.100.5'
          - '203.0.113.10'
    
    # Safely remove a multi-line record.
    - gcdns_record:
        record: 'api.example.com'
        zone_id: 'example-com'
        state: absent
        type: A
        record_data:           # NOTE: All of the values must match exactly
          - '192.0.2.23'
          - '192.0.2.42'
          - '198.51.100.5'
          - '203.0.113.10'
    
    # Unconditionally remove a record.
    - gcdns_record:
        record: 'api.example.com'
        zone_id: 'example-com'
        state: absent
        overwrite: true   # overwrite is true, so no values are needed
        type: A
    
    # Create an AAAA record
    - gcdns_record:
        record: 'www1.example.com'
        zone: 'example.com'
        type: AAAA
        value: 'fd00:db8::1'
    
    # Create a PTR record
    - gcdns_record:
        record: '10.5.168.192.in-addr.arpa'
        zone: '5.168.192.in-addr.arpa'
        type: PTR
        value: 'api.example.com.'    # Note the trailing dot.
    
    # Create an NS record
    - gcdns_record:
        record: 'subdomain.example.com'
        zone: 'example.com'
        type: NS
        ttl: 21600
        record_data:
          - 'ns-cloud-d1.googledomains.com.'    # Note the trailing dots on values
          - 'ns-cloud-d2.googledomains.com.'
          - 'ns-cloud-d3.googledomains.com.'
          - 'ns-cloud-d4.googledomains.com.'
    
    # Create a TXT record
    - gcdns_record:
        record: 'example.com'
        zone_id: 'example-com'
        type: TXT
        record_data:
          - '"v=spf1 include:_spf.google.com -all"'   # A single-string TXT value
          - '"hello " "world"'    # A multi-string TXT value

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
        <td> zone_id </td>
        <td> The Google Cloud DNS ID of the zone </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example-com </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> The dns name of the zone </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example.com. </td>
    </tr>
            <tr>
        <td> record </td>
        <td> Fully-qualified domain name of the resource record </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> mail.example.com. </td>
    </tr>
            <tr>
        <td> record_data </td>
        <td> The resource record values </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ['5.6.7.8', '9.10.11.12'] </td>
    </tr>
            <tr>
        <td> state </td>
        <td> Whether the record is present or absent </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> ttl </td>
        <td> The time-to-live of the resource record </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 300 </td>
    </tr>
            <tr>
        <td> type </td>
        <td> The type of the resource record </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> A </td>
    </tr>
            <tr>
        <td> overwrite </td>
        <td> Whether to the module was allowed to overwrite the record </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - See also :ref:`gcdns_zone <gcdns_zone>`.
    - This modules's underlying library does not support in-place updates for DNS resource records. Instead, resource records are quickly deleted and recreated.
    - SOA records are technically supported, but their functionality is limited to verifying that a zone's existing SOA record matches a pre-determined value. The SOA record cannot be updated.
    - Root NS records cannot be updated.
    - NAPTR records are not supported.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
