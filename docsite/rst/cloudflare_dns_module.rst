.. _cloudflare_dns:


cloudflare_dns - manage Cloudflare DNS records
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages dns records via the Cloudflare API, see the docs: https://api.cloudflare.com/


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
    <td>account_api_token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Account API token. You can obtain your API key from the bottom of the Cloudflare 'My Account' page, found here: <a href='https://www.cloudflare.com/a/account'>https://www.cloudflare.com/a/account</a></div></td></tr>
            <tr>
    <td>account_email<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Account email.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Service port. Required for <code>type=SRV</code></div></td></tr>
            <tr>
    <td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>Record priority. Required for <code>type=MX</code> and <code>type=SRV</code></div></td></tr>
            <tr>
    <td>proto<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>tcp</li><li>udp</li></ul></td>
        <td><div>Service protocol. Required for <code>type=SRV</code></div></td></tr>
            <tr>
    <td>record<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>@</td>
        <td><ul></ul></td>
        <td><div>Record to add. Required if <code>state=present</code>. Default is <code>@</code> (e.g. the zone name)</div></br>
        <div style="font-size: small;">aliases: name<div></td></tr>
            <tr>
    <td>service<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Record service. Required for <code>type=SRV</code></div></td></tr>
            <tr>
    <td>solo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether the record should be the only one for that record type and record name. Only use with <code>state=present</code></div><div>This will delete all other records with the same record name and type.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the record(s) should exist or not</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>Timeout for Cloudflare API calls</div></td></tr>
            <tr>
    <td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1 (automatic)</td>
        <td><ul></ul></td>
        <td><div>The TTL to give the new record. Must be between 120 and 2,147,483,647 seconds, or 1 for automatic.</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>A</li><li>AAAA</li><li>CNAME</li><li>TXT</li><li>SRV</li><li>MX</li><li>NS</li><li>SPF</li></ul></td>
        <td><div>The type of DNS record to create. Required if <code>state=present</code></div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The record value. Required for <code>state=present</code></div></br>
        <div style="font-size: small;">aliases: content<div></td></tr>
            <tr>
    <td>weight<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>Service weight. Required for <code>type=SRV</code></div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the Zone to work with (e.g. "example.com"). The Zone must already exist.</div></br>
        <div style="font-size: small;">aliases: domain<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # create a test.my.com A record to point to 127.0.0.1
    - cloudflare_dns:
        zone: my.com
        record: test
        type: A
        value: 127.0.0.1
        account_email: test@example.com
        account_api_token: dummyapitoken
      register: record
    
    # create a my.com CNAME record to example.com
    - cloudflare_dns:
        zone: my.com
        type: CNAME
        value: example.com
        state: present
        account_email: test@example.com
        account_api_token: dummyapitoken
    
    # change it's ttl
    - cloudflare_dns:
        zone: my.com
        type: CNAME
        value: example.com
        ttl: 600
        state: present
        account_email: test@example.com
        account_api_token: dummyapitoken
    
    # and delete the record
    - cloudflare_dns:
        zone: my.com
        type: CNAME
        value: example.com
        state: absent
        account_email: test@example.com
        account_api_token: dummyapitoken
    
    # create TXT record "test.my.com" with value "unique value"
    # delete all other TXT records named "test.my.com"
    - cloudflare_dns:
        domain: my.com
        record: test
        type: TXT
        value: unique value
        state: present
        solo: true
        account_email: test@example.com
        account_api_token: dummyapitoken
    
    # create a SRV record _foo._tcp.my.com
    - cloudflare_dns:
        domain: my.com
        service: foo
        proto: tcp
        port: 3500
        priority: 10
        weight: 20
        type: SRV
        value: fooserver.my.com

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
        <td> record </td>
        <td> dictionary containing the record data </td>
        <td align=center> success, except on record deletion </td>
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
        <td> proxiable </td>
        <td> whether this record can be proxied through cloudflare </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> locked </td>
        <td> No documentation available </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> name </td>
        <td> the record name as FQDN (including _service and _proto for SRV) </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> www.sample.com </td>
        </tr>
                <tr>
        <td> data </td>
        <td> additional record data </td>
        <td align=center> success, if type is SRV </td>
        <td align=center> dictionary </td>
        <td align=center> {'priority': 10, 'target': 'jabberhost.sample.com', 'service': '_xmpp', 'proto': '_tcp', 'port': 8080, 'weight': 5, 'name': 'jabber'} </td>
        </tr>
                <tr>
        <td> proxied </td>
        <td> whether the record is proxied through cloudflare </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> priority </td>
        <td> priority of the MX record </td>
        <td align=center> success, if type is MX </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
        </tr>
                <tr>
        <td> created_on </td>
        <td> the record creation date </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2016-03-25 19:09:42.516553 </td>
        </tr>
                <tr>
        <td> meta </td>
        <td> No documentation available </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center> {'auto_added': False} </td>
        </tr>
                <tr>
        <td> ttl </td>
        <td> the time-to-live for the record </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 300 </td>
        </tr>
                <tr>
        <td> modified_on </td>
        <td> record modification date </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2016-03-25 19:09:42.516553 </td>
        </tr>
                <tr>
        <td> zone_name </td>
        <td> the name of the zone containing the record </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> sample.com </td>
        </tr>
                <tr>
        <td> content </td>
        <td> the record content (details depend on record type) </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 192.0.2.91 </td>
        </tr>
                <tr>
        <td> type </td>
        <td> the record type </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> A </td>
        </tr>
                <tr>
        <td> id </td>
        <td> the record id </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> f9efb0549e96abcb750de63b38c9576e </td>
        </tr>
                <tr>
        <td> zone_id </td>
        <td> the id of the zone containing the record </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> abcede0bf9f0066f94029d2e6b73856a </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

