.. _dnsimple:


dnsimple - Interface with dnsimple.com (a DNS hosting service).
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages domains and records via the DNSimple API, see the docs: http://developer.dnsimple.com/


Requirements (on host that executes module)
-------------------------------------------

  * dnsimple


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
                <tr><td>account_api_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Account API token. See <em>account_email</em> for info.</div>        </td></tr>
                <tr><td>account_email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Account email. If omitted, the env variables DNSIMPLE_EMAIL and DNSIMPLE_API_TOKEN will be looked for. If those aren't found, a <code>.dnsimple</code> file will be looked for, see: <a href='https://github.com/mikemaccana/dnsimple-python#getting-started'>https://github.com/mikemaccana/dnsimple-python#getting-started</a></div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain to work with. Can be the domain name (e.g. "mydomain.com") or the numeric ID of the domain in DNSimple. If omitted, a list of domains will be returned.</div><div>If domain is present but the domain doesn't exist, it will be created.</div>        </td></tr>
                <tr><td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Record priority</div>        </td></tr>
                <tr><td>record<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Record to add, if blank a record for the domain will be created, supports the wildcard (*)</div>        </td></tr>
                <tr><td>record_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of records to ensure they either exist or don't exist</div>        </td></tr>
                <tr><td>solo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether the record should be the only one for that record type and record name. Only use with state=present on a record</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>whether the record should exist or not</div>        </td></tr>
                <tr><td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3600 (one hour)</td>
        <td></td>
        <td><div>The TTL to give the new record</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>A</li><li>ALIAS</li><li>CNAME</li><li>MX</li><li>SPF</li><li>URL</li><li>TXT</li><li>NS</li><li>SRV</li><li>NAPTR</li><li>PTR</li><li>AAAA</li><li>SSHFP</li><li>HINFO</li><li>POOL</li></ul></td>
        <td><div>The type of DNS record to create</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Record value</div><div>Must be specified when trying to ensure a record exists</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # authenticate using email and API token and fetch all domains
    - dnsimple:
        account_email: test@example.com
        account_api_token: dummyapitoken
      delegate_to: localhost
    
    # fetch my.com domain records
    - dnsimple:
        domain: my.com
        state: present
      delegate_to: localhost
      register: records
    
    # delete a domain
    - dnsimple:
        domain: my.com
        state: absent
      delegate_to: localhost
    
    # create a test.my.com A record to point to 127.0.0.01
    - dnsimple:
        domain: my.com
        record: test
        type: A
        value: 127.0.0.1
      delegate_to: localhost
      register: record
    
    # and then delete it
    - dnsimple:
        domain: my.com
        record_ids: '{{ record["id"] }}'
      delegate_to: localhost
    
    # create a my.com CNAME record to example.com
    - dnsimple:
        domain: my.com
        record: ''
        type: CNAME
        value: example.com
        state: present
      delegate_to: localhost
    
    # change it's ttl
    - dnsimple:
        domain: my.com
        record: ''
        type: CNAME
        value: example.com
        ttl: 600
        state: present
      delegate_to: localhost
    
    # and delete the record
    - dnsimple:
        domain: my.com
        record: ''
        type: CNAME
        value: example.com
        state: absent
      delegate_to: localhost





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
