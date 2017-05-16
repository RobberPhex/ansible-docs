.. _rax_dns_record:


rax_dns_record - Manage DNS records on Rackspace Cloud DNS
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

Manage DNS records on Rackspace Cloud DNS

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
    <td>api_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rackspace API key (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>comment</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Brief description of the domain. Maximum length of 160 characters</td>
    </tr>
            <tr>
    <td>credentials</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</td>
    </tr>
            <tr>
    <td>data</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>IP address for A/AAAA record, FQDN for CNAME/MX/NS, or text data for SRV/TXT</td>
    </tr>
            <tr>
    <td>domain</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Domain name to create the record in. This is an invalid option when type=PTR</td>
    </tr>
            <tr>
    <td>env</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a> (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>loadbalancer</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Load Balancer ID to create a PTR record for. Only used with type=PTR (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>FQDN record name to create</td>
    </tr>
            <tr>
    <td>priority</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Required for MX and SRV records, but forbidden for other record types. If specified, must be an integer from 0 to 65535.</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td>Region to create an instance in</td>
    </tr>
            <tr>
    <td>server</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Server ID to create a PTR record for. Only used with type=PTR (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>ttl</td>
    <td>no</td>
    <td>3600</td>
        <td><ul></ul></td>
        <td>Time to live of record in seconds</td>
    </tr>
            <tr>
    <td>type</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>A</li><li>AAAA</li><li>CNAME</li><li>MX</li><li>NS</li><li>SRV</li><li>TXT</li><li>PTR</li></ul></td>
        <td>DNS record type</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rackspace username (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>verify_ssl</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether or not to require SSL validation of API endpoints (added in Ansible 1.5)</td>
    </tr>
        </table>


.. note:: Requires pyrax


Examples
--------

.. raw:: html

    <br/>


::

    - name: Create DNS Records
      hosts: all
      gather_facts: False
      tasks:
        - name: Create A record
          local_action:
            module: rax_dns_record
            credentials: ~/.raxpub
            domain: example.org
            name: www.example.org
            data: "{{ rax_accessipv4 }}"
            type: A
          register: a_record
    
        - name: Create PTR record
          local_action:
            module: rax_dns_record
            credentials: ~/.raxpub
            server: "{{ rax_id }}"
            name: "{{ inventory_hostname }}"
            region: DFW
          register: ptr_record

.. note:: It is recommended that plays utilizing this module be run with ``serial: 1`` to avoid exceeding the API request limit imposed by the Rackspace CloudDNS API
.. note:: To manipulate a ``PTR`` record either ``loadbalancer`` or ``server`` must be supplied
.. note:: As of version 1.7, the ``type`` field is required and no longer defaults to an ``A`` record.
.. note:: ``PTR`` record support was added in version 1.7
.. note:: The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
.. note:: ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
.. note:: ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
.. note:: ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

