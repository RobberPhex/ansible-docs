.. _dnsimple:


dnsimple - Interface with dnsimple.com (a DNS hosting service).
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Manages domains and records via the DNSimple API, see the docs: http://developer.dnsimple.com/

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
    <td>account_api_token</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Account API token. See <em>account_email</em> for info.</td>
    </tr>
            <tr>
    <td>account_email</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Account email. If omitted, the env variables DNSIMPLE_EMAIL and DNSIMPLE_API_TOKEN will be looked for. If those aren't found, a <code>.dnsimple</code> file will be looked for, see: <a href='https://github.com/mikemaccana/dnsimple-python#getting-started'>https://github.com/mikemaccana/dnsimple-python#getting-started</a></td>
    </tr>
            <tr>
    <td>domain</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Domain to work with. Can be the domain name (e.g. "mydomain.com") or the numeric ID of the domain in DNSimple. If omitted, a list of domains will be returned.If domain is present but the domain doesn't exist, it will be created.</td>
    </tr>
            <tr>
    <td>priority</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Record priority</td>
    </tr>
            <tr>
    <td>record</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Record to add, if blank a record for the domain will be created, supports the wildcard (*)</td>
    </tr>
            <tr>
    <td>record_ids</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of records to ensure they either exist or don't exist</td>
    </tr>
            <tr>
    <td>solo</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether the record should be the only one for that record type and record name. Only use with state=present on a record</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>whether the record should exist or not</td>
    </tr>
            <tr>
    <td>ttl</td>
    <td>no</td>
    <td>3600 (one hour)</td>
        <td><ul></ul></td>
        <td>The TTL to give the new record</td>
    </tr>
            <tr>
    <td>type</td>
    <td>no</td>
    <td></td>
        <td><ul><li>A</li><li>ALIAS</li><li>CNAME</li><li>MX</li><li>SPF</li><li>URL</li><li>TXT</li><li>NS</li><li>SRV</li><li>NAPTR</li><li>PTR</li><li>AAAA</li><li>SSHFP</li><li>HINFO</li><li>POOL</li></ul></td>
        <td>The type of DNS record to create</td>
    </tr>
            <tr>
    <td>value</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Record valueMust be specified when trying to ensure a record exists</td>
    </tr>
        </table>


.. note:: Requires dnsimple


Examples
--------

.. raw:: html

    <br/>


::

    # authenticate using email and API token
    - local_action: dnsimple account_email=test@example.com account_api_token=dummyapitoken
    
    # fetch all domains
    - local_action dnsimple
      register: domains
    
    # fetch my.com domain records
    - local_action: dnsimple domain=my.com state=present
      register: records
    
    # delete a domain
    - local_action: dnsimple domain=my.com state=absent
    
    # create a test.my.com A record to point to 127.0.0.01
    - local_action: dnsimple domain=my.com record=test type=A value=127.0.0.1
      register: record
    
    # and then delete it
    - local_action: dnsimple domain=my.com record_ids={{ record['id'] }}
    
    # create a my.com CNAME record to example.com
    - local_action: dnsimple domain=my.com record= type=CNAME value=example.com state=present
    
    # change it's ttl
    - local_action: dnsimple domain=my.com record= type=CNAME value=example.com ttl=600 state=present
    
    # and delete the record
    - local_action: dnsimpledomain=my.com record= type=CNAME value=example.com state=absent
    



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

