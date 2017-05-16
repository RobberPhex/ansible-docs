.. _dnsmadeeasy:


dnsmadeeasy - Interface with dnsmadeeasy.com (a DNS hosting service).
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages DNS records via the v2 REST API of the DNS Made Easy service.  It handles records only; there is no manipulation of domains or monitor/account support yet. See: http://www.dnsmadeeasy.com/services/rest-api/


Requirements (on host that executes module)
-------------------------------------------

  * hashlib
  * hmac


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
    <td>account_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Accout API Key.</div></td></tr>
            <tr>
    <td>account_secret<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Accout Secret Key.</div></td></tr>
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Domain to work with. Can be the domain name (e.g. "mydomain.com") or the numeric ID of the domain in DNS Made Easy (e.g. "839989") for faster resolution.</div></td></tr>
            <tr>
    <td>record_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Record name to get/create/delete/update. If record_name is not specified; all records for the domain will be returned in "result" regardless of the state argument.</div></td></tr>
            <tr>
    <td>record_ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1800</td>
        <td><ul></ul></td>
        <td><div>record's "Time to live".  Number of seconds the record remains cached in DNS servers.</div></td></tr>
            <tr>
    <td>record_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>A</li><li>AAAA</li><li>CNAME</li><li>HTTPRED</li><li>MX</li><li>NS</li><li>PTR</li><li>SRV</li><li>TXT</li></ul></td>
        <td><div>Record type.</div></td></tr>
            <tr>
    <td>record_value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Record value. HTTPRED: &lt;redirection URL&gt;, MX: &lt;priority&gt; &lt;target name&gt;, NS: &lt;name server&gt;, PTR: &lt;target name&gt;, SRV: &lt;priority&gt; &lt;weight&gt; &lt;port&gt; &lt;target name&gt;, TXT: &lt;text value&gt;</div><div>If record_value is not specified; no changes will be made and the record will be returned in 'result' (in other words, this module can be used to fetch a record's current id, type, and ttl)</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>whether the record should exist or not</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # fetch my.com domain records
    - dnsmadeeasy: account_key=key account_secret=secret domain=my.com state=present
      register: response
      
    # create / ensure the presence of a record
    - dnsmadeeasy: account_key=key account_secret=secret domain=my.com state=present record_name="test" record_type="A" record_value="127.0.0.1"
    
    # update the previously created record
    - dnsmadeeasy: account_key=key account_secret=secret domain=my.com state=present record_name="test" record_value="192.168.0.1"
    
    # fetch a specific record
    - dnsmadeeasy: account_key=key account_secret=secret domain=my.com state=present record_name="test"
      register: response
      
    # delete a record / ensure it is absent
    - dnsmadeeasy: account_key=key account_secret=secret domain=my.com state=absent record_name="test"


Notes
-----

.. note:: The DNS Made Easy service requires that machines interacting with the API have the proper time and timezone set. Be sure you are within a few seconds of actual time by using NTP.
.. note:: This module returns record(s) in the "result" element when 'state' is set to 'present'. This value can be be registered and used in your playbooks.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

