.. _dnsmadeeasy:


dnsmadeeasy - Interface with dnsmadeeasy.com (a DNS hosting service).
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Manages DNS records via the v2 REST API of the DNS Made Easy service.  It handles records only; there is no manipulation of domains or monitor/account support yet. See: http://www.dnsmadeeasy.com/services/rest-api/

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
    <td>account_key</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Accout API Key.</td>
    </tr>
            <tr>
    <td>account_secret</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Accout Secret Key.</td>
    </tr>
            <tr>
    <td>domain</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Domain to work with. Can be the domain name (e.g. "mydomain.com") or the numeric ID of the domain in DNS Made Easy (e.g. "839989") for faster resolution.</td>
    </tr>
            <tr>
    <td>record_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Record name to get/create/delete/update. If record_name is not specified; all records for the domain will be returned in "result" regardless of the state argument.</td>
    </tr>
            <tr>
    <td>record_ttl</td>
    <td>no</td>
    <td>1800</td>
        <td><ul></ul></td>
        <td>record's "Time to live".  Number of seconds the record remains cached in DNS servers.</td>
    </tr>
            <tr>
    <td>record_type</td>
    <td>no</td>
    <td></td>
        <td><ul><li>A</li><li>AAAA</li><li>CNAME</li><li>HTTPRED</li><li>MX</li><li>NS</li><li>PTR</li><li>SRV</li><li>TXT</li></ul></td>
        <td>Record type.</td>
    </tr>
            <tr>
    <td>record_value</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Record value. HTTPRED: &lt;redirection URL&gt;, MX: &lt;priority&gt; &lt;target name&gt;, NS: &lt;name server&gt;, PTR: &lt;target name&gt;, SRV: &lt;priority&gt; &lt;weight&gt; &lt;port&gt; &lt;target name&gt;, TXT: &lt;text value&gt;If record_value is not specified; no changes will be made and the record will be returned in 'result' (in other words, this module can be used to fetch a record's current id, type, and ttl)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>whether the record should exist or not</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates. (added in Ansible 1.5.1)</td>
    </tr>
        </table>


.. note:: Requires hashlib


.. note:: Requires hmac


Examples
--------

.. raw:: html

    <br/>


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

.. note:: The DNS Made Easy service requires that machines interacting with the API have the proper time and timezone set. Be sure you are within a few seconds of actual time by using NTP.
.. note:: This module returns record(s) in the "result" element when 'state' is set to 'present'. This value can be be registered and used in your playbooks.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

