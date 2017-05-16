.. _rax_clb:


rax_clb - create / delete a load balancer in Rackspace Public Cloud
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* creates / deletes a Rackspace Public Cloud load balancer.


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
                <tr><td>algorithm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>LEAST_CONNECTIONS</td>
        <td><ul><li>RANDOM</li><li>LEAST_CONNECTIONS</li><li>ROUND_ROBIN</li><li>WEIGHTED_LEAST_CONNECTIONS</li><li>WEIGHTED_ROUND_ROBIN</li></ul></td>
        <td><div>algorithm for the balancer being created</div>        </td></tr>
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace API key, overrides <em>credentials</em>.</div></br>
    <div style="font-size: small;">aliases: password<div>        </td></tr>
                <tr><td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>File to find the Rackspace credentials in. Ignored if <em>api_key</em> and <em>username</em> are provided.</div></br>
    <div style="font-size: small;">aliases: creds_file<div>        </td></tr>
                <tr><td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Environment as configured in <em>~/.pyrax.cfg</em>, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a>.</div>        </td></tr>
                <tr><td>meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash of metadata to associate with the instance</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name to give the load balancer</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>80</td>
        <td></td>
        <td><div>Port for the balancer being created</div>        </td></tr>
                <tr><td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>HTTP</td>
        <td><ul><li>DNS_TCP</li><li>DNS_UDP</li><li>FTP</li><li>HTTP</li><li>HTTPS</li><li>IMAPS</li><li>IMAPv4</li><li>LDAP</li><li>LDAPS</li><li>MYSQL</li><li>POP3</li><li>POP3S</li><li>SMTP</li><li>TCP</li><li>TCP_CLIENT_FIRST</li><li>UDP</li><li>UDP_STREAM</li><li>SFTP</li></ul></td>
        <td><div>Protocol for the balancer being created</div>        </td></tr>
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
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td></td>
        <td><div>timeout for communication between the balancer and the node</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>PUBLIC</td>
        <td><ul><li>PUBLIC</li><li>SERVICENET</li></ul></td>
        <td><div>type of interface for the balancer being created</div>        </td></tr>
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
                <tr><td>vip_id<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Virtual IP ID to use when creating the load balancer for purposes of sharing an IP with another load balancer of another protocol</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the balancer to be in state 'running' before returning</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>how long before wait gives up, in seconds</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Build a Load Balancer
      gather_facts: False
      hosts: local
      connection: local
      tasks:
        - name: Load Balancer create request
          local_action:
            module: rax_clb
            credentials: ~/.raxpub
            name: my-lb
            port: 8080
            protocol: HTTP
            type: SERVICENET
            timeout: 30
            region: DFW
            wait: yes
            state: present
            meta:
              app: my-cool-app
          register: my_lb


Notes
-----

.. note::
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
