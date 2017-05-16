.. _rax_dns:


rax_dns - Manage domains on Rackspace Cloud DNS
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage domains on Rackspace Cloud DNS


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * pyrax


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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace API key, overrides <em>credentials</em>.</div></br>
    <div style="font-size: small;">aliases: password<div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Brief description of the domain. Maximum length of 160 characters</div>        </td></tr>
                <tr><td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>File to find the Rackspace credentials in. Ignored if <em>api_key</em> and <em>username</em> are provided.</div></br>
    <div style="font-size: small;">aliases: creds_file<div>        </td></tr>
                <tr><td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Email address of the domain administrator</div>        </td></tr>
                <tr><td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Environment as configured in <em>~/.pyrax.cfg</em>, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a>.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain name to create</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td></td>
        <td><div>Region to create an instance in.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div>        </td></tr>
                <tr><td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3600</td>
        <td></td>
        <td><div>Time to live of domain in seconds</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace username, overrides <em>credentials</em>.</div>        </td></tr>
                <tr><td>verify_ssl<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not to require SSL validation of API endpoints.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create domain
      hosts: all
      gather_facts: False
      tasks:
        - name: Domain create request
          local_action:
            module: rax_dns
            credentials: ~/.raxpub
            name: example.org
            email: admin@example.org
          register: rax_dns


Notes
-----

.. note::
    - It is recommended that plays utilizing this module be run with ``serial: 1`` to avoid exceeding the API request limit imposed by the Rackspace CloudDNS API
    - The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
    - ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
    - ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
    - ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
