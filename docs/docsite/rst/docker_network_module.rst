.. _docker_network:


docker_network - Manage Docker networks
+++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create/remove Docker networks and connect containers to them.
* Performs largely the same function as the "docker network" CLI subcommand.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * docker-py >= 1.7.0
  * The docker server >= 1.9.0


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
                <tr><td>api_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>default provided by docker-py</td>
        <td></td>
        <td><div>The version of the Docker API running on the Docker Host. Defaults to the latest version of the API supported by docker-py.</div></br>
    <div style="font-size: small;">aliases: docker_api_version<div>        </td></tr>
                <tr><td>appends<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>By default the connected list is canonical, meaning containers not on the list are removed from the network. Use <code>appends</code> to leave existing containers connected.</div></br>
    <div style="font-size: small;">aliases: incremental<div>        </td></tr>
                <tr><td>cacert_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Use a CA certificate when performing server verification by providing the path to a CA certificate file.</div></br>
    <div style="font-size: small;">aliases: tls_ca_cert<div>        </td></tr>
                <tr><td>cert_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to the client's TLS certificate file.</div></br>
    <div style="font-size: small;">aliases: tls_client_cert<div>        </td></tr>
                <tr><td>connected<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of container names or container IDs to connect to a network.</div></br>
    <div style="font-size: small;">aliases: containers<div>        </td></tr>
                <tr><td>docker_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>unix://var/run/docker.sock</td>
        <td></td>
        <td><div>The URL or Unix socket path used to connect to the Docker API. To connect to a remote host, provide the TCP connection string. For example, 'tcp://192.0.2.23:2376'. If TLS is used to encrypt the connection, the module will automatically replace 'tcp' in the connection URL with 'https'.</div></br>
    <div style="font-size: small;">aliases: docker_url<div>        </td></tr>
                <tr><td>driver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>bridge</td>
        <td></td>
        <td><div>Specify the type of network. Docker provides bridge and overlay drivers, but 3rd party drivers can also be used.</div>        </td></tr>
                <tr><td>driver_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary of network settings. Consult docker docs for valid options and values.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>With state <em>absent</em> forces disconnecting all containers from the network prior to deleting the network. With state <em>present</em> will disconnect all containers, delete the network and re-create the network.  This option is required if you have changed the IPAM or driver options and want an existing network to be updated to use the new options.</div>        </td></tr>
                <tr><td>ipam_driver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify an IPAM driver.</div>        </td></tr>
                <tr><td>ipam_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary of IPAM options.</div>        </td></tr>
                <tr><td>key_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to the client's TLS key file.</div></br>
    <div style="font-size: small;">aliases: tls_client_key<div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the network to operate on.</div></br>
    <div style="font-size: small;">aliases: network_name<div>        </td></tr>
                <tr><td>ssl_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1.0</td>
        <td></td>
        <td><div>Provide a valid SSL version number. Default value determined by docker-py, currently 1.0.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div><em>absent</em> deletes the network. If a network has connected containers, it cannot be deleted. Use the <code>force</code> option to disconnect all containers and delete the network.</div><div><em>present</em> creates the network, if it does not already exist with the specified parameters, and connects the list of containers provided via the connected parameter. Containers not on the list will be disconnected. An empty list will leave no containers connected to the network. Use the <code>appends</code> option to leave existing containers connected. Use the <code>force</code> options to force re-creation of the network.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>60</td>
        <td></td>
        <td><div>The maximum amount of time in seconds to wait on a response from the API.</div>        </td></tr>
                <tr><td>tls<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secure the connection to the API by using TLS without verifying the authenticity of the Docker host server.</div>        </td></tr>
                <tr><td>tls_hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>When verifying the authenticity of the Docker Host server, provide the expected name of the server.</div>        </td></tr>
                <tr><td>tls_verify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secure the connection to the API by using TLS and verifying the authenticity of the Docker host server.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a network
      docker_network:
        name: network_one
    
    - name: Remove all but selected list of containers
      docker_network:
        name: network_one
        connected:
          - container_a
          - container_b
          - container_c
    
    - name: Remove a single container
      docker_network:
        name: network_one
        connected: "{{ fulllist|difference(['container_a']) }}"
    
    - name: Add a container to a network, leaving existing containers connected
      docker_network:
        name: network_one
        connected:
          - container_a
        appends: yes
    
    - name: Create a network with options
      docker_network:
        name: network_two
        driver_options:
          com.docker.network.bridge.name: net2
        ipam_options:
          subnet: '172.3.26.0/16'
          gateway: 172.3.26.1
          iprange: '192.168.1.0/24'
    
    - name: Delete a network, disconnecting all containers
      docker_network:
        name: network_one
        state: absent
        force: yes

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
        <td> facts </td>
        <td> Network inspection results for the affected network. </td>
        <td align=center> success </td>
        <td align=center> complex </td>
        <td align=center> {} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Connect to the Docker daemon by providing parameters with each task or by defining environment variables. You can define DOCKER_HOST, DOCKER_TLS_HOSTNAME, DOCKER_API_VERSION, DOCKER_CERT_PATH, DOCKER_SSL_VERSION, DOCKER_TLS, DOCKER_TLS_VERIFY and DOCKER_TIMEOUT. If you are using docker machine, run the script shipped with the product that sets up the environment. It will set these variables for you. See https://docker-py.readthedocs.org/en/stable/machine/ for more details.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
