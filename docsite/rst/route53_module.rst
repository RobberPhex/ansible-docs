.. _route53:


route53 - add or delete entries in Amazons Route53 DNS service
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Creates and deletes DNS records in Amazons Route53 service

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
    <td>alias</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Indicates if this is an alias record. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>alias_hosted_zone_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The hosted zone identifier. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>aws_access_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS access key.</td>
    </tr>
            <tr>
    <td>aws_secret_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS secret key.</td>
    </tr>
            <tr>
    <td>command</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>get</li><li>create</li><li>delete</li></ul></td>
        <td>Specifies the action to take.</td>
    </tr>
            <tr>
    <td>overwrite</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether an existing record should be overwritten on create if values do not match</td>
    </tr>
            <tr>
    <td>private_zone</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If set to true, the private zone matching the requested name within the domain will be used if there are both public and private zones. The default is to use the public zone. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>record</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The full DNS record to create or delete</td>
    </tr>
            <tr>
    <td>retry_interval</td>
    <td>no</td>
    <td>500</td>
        <td><ul></ul></td>
        <td>In the case that route53 is still servicing a prior request, this module will wait and try again after this many seconds. If you have many domain names, the default of 500 seconds may be too long.</td>
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
    <td>yes</td>
    <td></td>
        <td><ul><li>A</li><li>CNAME</li><li>MX</li><li>AAAA</li><li>TXT</li><li>PTR</li><li>SRV</li><li>SPF</li><li>NS</li></ul></td>
        <td>The type of DNS record to create</td>
    </tr>
            <tr>
    <td>value</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The new value when creating a DNS record.  Multiple comma-spaced values are allowed for non-alias records.  When deleting a record all values for the record must be specified or Route53 will not delete it.</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The DNS zone to modify</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    # Add new.foo.com as an A record with 3 IPs
    - route53:
          command: create
          zone: foo.com
          record: new.foo.com
          type: A
          ttl: 7200
          value: 1.1.1.1,2.2.2.2,3.3.3.3
    
    # Retrieve the details for new.foo.com
    - route53:
          command: get
          zone: foo.com
          record: new.foo.com
          type: A
      register: rec
    
    # Delete new.foo.com A record using the results from the get command
    - route53:
          command: delete
          zone: foo.com
          record: "{{ rec.set.record }}"
          ttl: "{{ rec.set.ttl }}"
          type: "{{ rec.set.type }}"
          value: "{{ rec.set.value }}"
    
    # Add an AAAA record.  Note that because there are colons in the value
    # that the entire parameter list must be quoted:
    - route53:
          command: "create"
          zone: "foo.com"
          record: "localhost.foo.com"
          type: "AAAA"
          ttl: "7200"
          value: "::1"
    
    # Add a TXT record. Note that TXT and SPF records must be surrounded
    # by quotes when sent to Route 53:
    - route53:
          command: "create"
          zone: "foo.com"
          record: "localhost.foo.com"
          type: "TXT"
          ttl: "7200"
          value: '"bar"'
    
    # Add an alias record that points to an Amazon ELB:
    - route53:
          command=create
          zone=foo.com
          record=elb.foo.com
          type=A
          value="{{ elb_dns_name }}"
          alias=yes
          alias_hosted_zone_id="{{ elb_zone_id }}"
    
    



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

