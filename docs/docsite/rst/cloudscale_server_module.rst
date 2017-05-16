.. _cloudscale_server:


cloudscale_server - Manages servers on the cloudscale.ch IaaS service
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, start, stop and delete servers on the cloudscale.ch IaaS service.
* All operations are performed using the cloudscale.ch public API v1.
* For details consult the full API documentation: https://www.cloudscale.ch/en/api/v1.
* An valid API token is required for all operations. You can create as many tokens as you like using the cloudscale.ch control panel at https://control.cloudscale.ch.




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
                <tr><td>anti_affinity_with<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>UUID of another server to create an anti-affinity group with</div>        </td></tr>
                <tr><td>api_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>cloudscale.ch API token.</div><div>This can also be passed in the CLOUDSCALE_API_TOKEN environment variable.</div>        </td></tr>
                <tr><td>bulk_volume_size_gb<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>null (no bulk storage volume)</td>
        <td></td>
        <td><div>Size of the bulk storage volume in GB</div>        </td></tr>
                <tr><td>flavor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Flavor of the server</div>        </td></tr>
                <tr><td>image<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Image used to create the server</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the Server</div><div>Either <code>name</code> or <code>uuid</code> are required. These options are mutually exclusive.</div>        </td></tr>
                <tr><td>ssh_keys<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of SSH public keys</div><div>Use the full content of your .pub file here.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>running</td>
        <td><ul><li>running</li><li>stopped</li><li>absent</li></ul></td>
        <td><div>State of the server</div>        </td></tr>
                <tr><td>use_ipv6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Enable IPv6 on the public network interface</div>        </td></tr>
                <tr><td>use_private_network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Attach a private network interface to the server</div>        </td></tr>
                <tr><td>use_public_network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Attach a public network interface to the server</div>        </td></tr>
                <tr><td>user_data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Cloud-init configuration (cloud-config) data to use for the server.</div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>UUID of the server</div><div>Either <code>name</code> or <code>uuid</code> are required. These options are mutually exclusive.</div>        </td></tr>
                <tr><td>volume_size_gb<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Size of the root volume in GB</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Start a server (if it does not exist) and register the server details
    - name: Start cloudscale.ch server
      cloudscale_server:
        name: my-shiny-cloudscale-server
        image: debian-8
        flavor: flex-4
        ssh_keys: ssh-rsa XXXXXXXXXX...XXXX ansible@cloudscale
        use_private_network: True
        bulk_volume_size_gb: 100
        api_token: xxxxxx
      register: server1
    
    # Start another server in anti-affinity to the first one
    - name: Start second cloudscale.ch server
      cloudscale_server:
        name: my-other-shiny-server
        image: ubuntu-16.04
        flavor: flex-8
        ssh_keys: ssh-rsa XXXXXXXXXXX ansible@cloudscale
        anti_affinity_with: '{{ server1.uuid }}'
        api_token: xxxxxx
    
    # Stop the first server
    - name: Stop my first server
      cloudscale_server:
        uuid: '{{ server1.uuid }}'
        state: stopped
        api_token: xxxxxx
    
    # Delete my second server
    - name: Delete my second server
      cloudscale_server:
        name: my-other-shiny-server
        state: absent
        api_token: xxxxxx
    
    # Start a server and wait for the SSH host keys to be generated
    - name: Start server and wait for SSH host keys
      cloudscale_server:
        name: my-cloudscale-server-with-ssh-key
        image: debian-8
        flavor: flex-4
        ssh_keys: ssh-rsa XXXXXXXXXXX ansible@cloudscale
        api_token: xxxxxx
      register: server
      until: server.ssh_fingerprints
      retries: 60
      delay: 2

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
        <td> uuid </td>
        <td> The unique identifier for this server </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> cfde831a-4e87-4a75-960f-89b0148aa2cc </td>
    </tr>
            <tr>
        <td> image </td>
        <td> The image used for booting this server </td>
        <td align=center> success when not state == absent </td>
        <td align=center> string </td>
        <td align=center> debian-8 </td>
    </tr>
            <tr>
        <td> state </td>
        <td> The current status of the server </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> running </td>
    </tr>
            <tr>
        <td> name </td>
        <td> The display name of the server </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> its-a-me-mario.cloudscale.ch </td>
    </tr>
            <tr>
        <td> anti_affinity_with </td>
        <td> List of servers in the same anti-affinity group </td>
        <td align=center> success when not state == absent </td>
        <td align=center> string </td>
        <td align=center> [] </td>
    </tr>
            <tr>
        <td> ssh_fingerprints </td>
        <td> A list of SSH host key fingerprints. Will be null until the host keys could be retrieved from the server. </td>
        <td align=center> success when not state == absent </td>
        <td align=center> list </td>
        <td align=center> ['ecdsa-sha2-nistp256 SHA256:XXXX', '...'] </td>
    </tr>
            <tr>
        <td> href </td>
        <td> API URL to get details about this server </td>
        <td align=center> success when not state == absent </td>
        <td align=center> string </td>
        <td align=center> https://api.cloudscale.ch/v1/servers/cfde831a-4e87-4a75-960f-89b0148aa2cc </td>
    </tr>
            <tr>
        <td> volumes </td>
        <td> List of volumes attached to the server </td>
        <td align=center> success when not state == absent </td>
        <td align=center> list </td>
        <td align=center> [{'device': '/dev/vda', 'size_gb': '50', 'type': 'ssd'}] </td>
    </tr>
            <tr>
        <td> flavor </td>
        <td> The flavor that has been used for this server </td>
        <td align=center> success when not state == absent </td>
        <td align=center> string </td>
        <td align=center> flex-8 </td>
    </tr>
            <tr>
        <td> interfaces </td>
        <td> List of network ports attached to the server </td>
        <td align=center> success when not state == absent </td>
        <td align=center> list </td>
        <td align=center> [{'type': 'public', 'addresses': ['...']}] </td>
    </tr>
            <tr>
        <td> ssh_host_keys </td>
        <td> A list of SSH host keys. Will be null until the host keys could be retrieved from the server. </td>
        <td align=center> success when not state == absent </td>
        <td align=center> list </td>
        <td align=center> ['ecdsa-sha2-nistp256 XXXXX', '...'] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Instead of the api_token parameter the CLOUDSCALE_API_TOKEN environment variable can be used.
    - To create a new server at least the ``name``, ``ssh_key``, ``image`` and ``flavor`` options are required.
    - If more than one server with the name given by the ``name`` option exists, execution is aborted.
    - Once a server is created all parameters except ``state`` are read-only. You can't change the name, flavor or any other property. This is a limitation of the cloudscale.ch API. The module will silently ignore differences between the configured parameters and the running server if a server with the correct name or UUID exists. Only state changes will be applied.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
