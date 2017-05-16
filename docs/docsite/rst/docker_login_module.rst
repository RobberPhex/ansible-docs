.. _docker_login:


docker_login - Log into a Docker registry.
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Provides functionality similar to the "docker login" command.
* Authenticate with a docker registry and add the credentials to your local Docker config file. Adding the credentials to the config files allows future connections to the registry using tools such as Ansible's Docker modules, the Docker CLI and docker-py without needing to provide credentials.
* Running in check mode will perform the authentication without updating the config file.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * docker-py >= 1.7.0
  * Docker API >= 1.20
  * Only to be able to logout (state=absent): the docker command line utility


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
                <tr><td>config_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>~/.docker/config.json</td>
        <td></td>
        <td><div>Custom path to the Docker CLI configuration file.</div></br>
    <div style="font-size: small;">aliases: self.config_path, dockercfg_path<div>        </td></tr>
                <tr><td>docker_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>unix://var/run/docker.sock</td>
        <td></td>
        <td><div>The URL or Unix socket path used to connect to the Docker API. To connect to a remote host, provide the TCP connection string. For example, 'tcp://192.0.2.23:2376'. If TLS is used to encrypt the connection, the module will automatically replace 'tcp' in the connection URL with 'https'.</div></br>
    <div style="font-size: small;">aliases: docker_url<div>        </td></tr>
                <tr><td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The email address for the registry account. NOTE: private registries may not require this, but Docker Hub requires it.</div>        </td></tr>
                <tr><td>key_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to the client's TLS key file.</div></br>
    <div style="font-size: small;">aliases: tls_client_key<div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The plaintext password for the registry account</div>        </td></tr>
                <tr><td>reauthorize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Refresh exiting authentication found in the configuration file.</div></br>
    <div style="font-size: small;">aliases: reauth<div>        </td></tr>
                <tr><td>registry_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://index.docker.io/v1/</td>
        <td></td>
        <td><div>The registry URL.</div></br>
    <div style="font-size: small;">aliases: registry, url<div>        </td></tr>
                <tr><td>ssl_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1.0</td>
        <td></td>
        <td><div>Provide a valid SSL version number. Default value determined by docker-py, currently 1.0.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>This controls the current state of the user. <code>present</code> will login in a user, <code>absent</code> will log him out.</div><div>To logout you only need the registry server, which defaults to DockerHub.</div><div>Before 2.1 you could ONLY log in.</div><div>docker does not support 'logout' with a custom config file.</div>        </td></tr>
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
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username for the registry account</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: Log into DockerHub
      docker_login:
        username: docker
        password: rekcod
        email: docker@docker.io
    
    - name: Log into private registry and force re-authorization
      docker_login:
        registry: your.private.registry.io
        username: yourself
        password: secrets3
        reauthorize: yes
    
    - name: Log into DockerHub using a custom config file
      docker_login:
        username: docker
        password: rekcod
        email: docker@docker.io
        config_path: /tmp/.mydockercfg
    
    - name: Log out of DockerHub
      docker_login:
        state: absent
        email: docker@docker.com

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
        <td> login_results </td>
        <td> Results from the login. </td>
        <td align=center> when state='present' </td>
        <td align=center> dict </td>
        <td align=center> {'username': 'testuser', 'password': 'VALUE_SPECIFIED_IN_NO_LOG_PARAMETER', 'email': 'testuer@yahoo.com', 'serveraddress': 'localhost:5000'} </td>
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
