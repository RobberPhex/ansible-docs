.. _docker_image_facts:


docker_image_facts - Inspect docker images
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Provide one or more image names, and the module will inspect each, returning an array of inspection results.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * docker-py >= 1.7.0
  * Docker API >= 1.20


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
                <tr><td>docker_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>unix://var/run/docker.sock</td>
        <td></td>
        <td><div>The URL or Unix socket path used to connect to the Docker API. To connect to a remote host, provide the TCP connection string. For example, 'tcp://192.0.2.23:2376'. If TLS is used to encrypt the connection, the module will automatically replace 'tcp' in the connection URL with 'https'.</div></br>
    <div style="font-size: small;">aliases: docker_url<div>        </td></tr>
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
        <td><div>An image name or a list of image names. Name format will be name[:tag] or repository/name[:tag], where tag is optional. If a tag is not provided, 'latest' will be used.</div>        </td></tr>
                <tr><td>ssl_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1.0</td>
        <td></td>
        <td><div>Provide a valid SSL version number. Default value determined by docker-py, currently 1.0.</div>        </td></tr>
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

    
    - name: Inspect a single image
      docker_image_facts:
        name: pacur/centos-7
    
    - name: Inspect multiple images
      docker_image_facts:
        name:
          - pacur/centos-7
          - sinatra

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
        <td> images </td>
        <td> Facts for the selected images. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> [{'Container': 'e83a452b8fb89d78a25a6739457050131ca5c863629a47639530d9ad2008d610', 'Name': 'registry:2', 'Author': '', 'GraphDriver': {'Data': None, 'Name': 'aufs'}, 'Architecture': 'amd64', 'VirtualSize': 165808884, 'ContainerConfig': {'Cmd': ['/bin/sh', '-c', '#(nop) CMD ["/etc/docker/registry/config.yml"]'], 'Env': ['PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin'], 'StdinOnce': False, 'Hostname': 'e5c68db50333', 'WorkingDir': '', 'Entrypoint': ['/bin/registry'], 'Volumes': {'/var/lib/registry': {}}, 'OnBuild': [], 'OpenStdin': False, 'Tty': False, 'Domainname': '', 'Image': 'c72dce2618dc8f7b794d2b2c2b1e64e0205ead5befc294f8111da23bd6a2c799', 'Labels': {}, 'ExposedPorts': {'5000/tcp': {}}, 'User': '', 'AttachStdin': False, 'AttachStderr': False, 'AttachStdout': False}, 'Os': 'linux', 'RepoTags': ['registry:2'], 'Comment': '', 'DockerVersion': '1.9.1', 'Parent': 'f0b1f729f784b755e7bf9c8c2e65d8a0a35a533769c2588f02895f6781ac0805', 'Config': {'Cmd': ['/etc/docker/registry/config.yml'], 'Env': ['PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin'], 'StdinOnce': False, 'Hostname': 'e5c68db50333', 'WorkingDir': '', 'Entrypoint': ['/bin/registry'], 'Volumes': {'/var/lib/registry': {}}, 'OnBuild': [], 'OpenStdin': False, 'Tty': False, 'Domainname': '', 'Image': 'c72dce2618dc8f7b794d2b2c2b1e64e0205ead5befc294f8111da23bd6a2c799', 'Labels': {}, 'ExposedPorts': {'5000/tcp': {}}, 'User': '', 'AttachStdin': False, 'AttachStderr': False, 'AttachStdout': False}, 'Created': '2016-03-08T21:08:15.399680378Z', 'RepoDigests': [], 'Id': '53773d8552f07b730f3e19979e32499519807d67b344141d965463a950a66e08', 'Size': 0}] </td>
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
