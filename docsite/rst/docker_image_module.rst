.. _docker_image:


docker_image - Manage docker images.
++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Build, load or pull an image, making the image available for creating containers. Also supports tagging an image into a repository and archiving an image to a .tar file.


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
            <tr>
    <td>api_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>default provided by docker-py</td>
        <td><ul></ul></td>
        <td><div>The version of the Docker API running on the Docker Host. Defaults to the latest version of the API supported by docker-py.</div></br>
        <div style="font-size: small;">aliases: docker_api_version<div></td></tr>
            <tr>
    <td>archive_path<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with state <code>present</code> to archive an image to a .tar file.</div></td></tr>
            <tr>
    <td>buildargs<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide a dictionary of <code>key:value</code> build arguments that map to Dockerfile ARG directive.</div><div>Docker expects the value to be a string. For convenience any non-string values will be converted to strings.</div><div>Requires Docker API &gt;= 1.21 and docker-py &gt;= 1.7.0.</div></td></tr>
            <tr>
    <td>cacert_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use a CA certificate when performing server verification by providing the path to a CA certificate file.</div></br>
        <div style="font-size: small;">aliases: tls_ca_cert<div></td></tr>
            <tr>
    <td>cert_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the client's TLS certificate file.</div></br>
        <div style="font-size: small;">aliases: tls_client_cert<div></td></tr>
            <tr>
    <td>container_limits<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary of limits applied to each container created by the build process.</div></td></tr>
            <tr>
    <td>docker_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>unix://var/run/docker.sock</td>
        <td><ul></ul></td>
        <td><div>The URL or Unix socket path used to connect to the Docker API. To connect to a remote host, provide the TCP connection string. For example, 'tcp://192.0.2.23:2376'. If TLS is used to encrypt the connection, the module will automatically replace 'tcp' in the connection URL with 'https'.</div></br>
        <div style="font-size: small;">aliases: docker_url<div></td></tr>
            <tr>
    <td>dockerfile<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>Dockerfile</td>
        <td><ul></ul></td>
        <td><div>Use with state <code>present</code> to provide an alternate name for the Dockerfile to use when building an image.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with state <em>absent</em> to un-tag and remove all images matching the specified name. Use with state <code>present</code> to build, load or pull an image when the image already exists.</div></td></tr>
            <tr>
    <td>http_timeout<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Timeout for HTTP requests during the image build operation. Provide a positive integer value for the number of seconds.</div></td></tr>
            <tr>
    <td>key_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the client's TLS key file.</div></br>
        <div style="font-size: small;">aliases: tls_client_key<div></td></tr>
            <tr>
    <td>load_path<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with state <code>present</code> to load an image from a .tar file.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Image name. Name format will be one of: name, repository/name, registry_server:port/name. When pushing or pulling an image the name can optionally include the tag by appending ':tag_name'.</div></td></tr>
            <tr>
    <td>nocache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Do not use cache when building an image.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with state 'present' to build an image. Will be the path to a directory containing the context and Dockerfile for building an image.</div></br>
        <div style="font-size: small;">aliases: build_path<div></td></tr>
            <tr>
    <td>pull<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>When building an image downloads any updates to the FROM image in Dockerfile.</div></td></tr>
            <tr>
    <td>push<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Push the image to the registry. Specify the registry as part of the <em>name</em> or <em>repository</em> parameter.</div></td></tr>
            <tr>
    <td>repository<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Full path to a repository. Use with state <code>present</code> to tag the image into the repository. Expects format <em>repository:tag</em>. If no tag is provided, will use the value of the <code>tag</code> parameter or <em>latest</em>.</div></td></tr>
            <tr>
    <td>rm<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Remove intermediate containers after build.</div></td></tr>
            <tr>
    <td>ssl_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1.0</td>
        <td><ul></ul></td>
        <td><div>Provide a valid SSL version number. Default value determined by docker-py, currently 1.0.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li><li>build</li></ul></td>
        <td><div>Make assertions about the state of an image.</div><div>When <code>absent</code> an image will be removed. Use the force option to un-tag and remove all images matching the provided name.</div><div>When <code>present</code> check if an image exists using the provided name and tag. If the image is not found or the force option is used, the image will either be pulled, built or loaded. By default the image will be pulled from Docker Hub. To build the image, provide a path value set to a directory containing a context and Dockerfile. To load an image, specify load_path to provide a path to an archive file. To tag an image to a repository, provide a repository path. If the name contains a repository path, it will be pushed.</div><div>NOTE: <code>build</code> is DEPRECATED and will be removed in release 2.3. Specifying <code>build</code> will behave the same as <code>present</code>.</div></td></tr>
            <tr>
    <td>tag<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>latest</td>
        <td><ul></ul></td>
        <td><div>Used to select an image when pulling. Will be added to the image when pushing, tagging or building. Defaults to <em>latest</em>.</div><div>If <code>name</code> parameter format is <em>name:tag</em>, then tag value from <code>name</code> will take precedence.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>60</td>
        <td><ul></ul></td>
        <td><div>The maximum amount of time in seconds to wait on a response from the API.</div></td></tr>
            <tr>
    <td>tls<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Secure the connection to the API by using TLS without verifying the authenticity of the Docker host server.</div></td></tr>
            <tr>
    <td>tls_hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>When verifying the authenticity of the Docker Host server, provide the expected name of the server.</div></td></tr>
            <tr>
    <td>tls_verify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Secure the connection to the API by using TLS and verifying the authenticity of the Docker host server.</div></td></tr>
            <tr>
    <td>use_tls<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>False</li><li>encrypt</li><li>verify</li></ul></td>
        <td><div>DEPRECATED. Whether to use tls to connect to the docker server. Set to <code>no</code> when TLS will not be used. Set to <code>encrypt</code> to use TLS. And set to <code>verify</code> to use TLS and verify that the server's certificate is valid for the server. NOTE: If you specify this option, it will set the value of the tls or tls_verify parameters.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: pull an image
      docker_image:
        name: pacur/centos-7
    
    - name: Tag and push to docker hub
      docker_image:
        name: pacur/centos-7
        repository: dcoppenhagan/myimage
        tag: 7.0
        push: yes
    
    - name: Tag and push to local registry
      docker_image:
         name: centos
         repository: localhost:5000/centos
         tag: 7
         push: yes
    
    - name: Remove image
      docker_image:
        state: absent
        name: registry.ansible.com/chouseknecht/sinatra
        tag: v1
    
    - name: Build an image ad push it to a private repo
      docker_image:
        path: ./sinatra
        name: registry.ansible.com/chouseknecht/sinatra
        tag: v1
    
    - name: Archive image
      docker_image:
        name: registry.ansible.com/chouseknecht/sinatra
        tag: v1
        archive_path: my_sinatra.tar
    
    - name: Load image from archive and push to a private registry
      docker_image:
        name: localhost:5000/myimages/sinatra
        tag: v1
        push: yes
        load_path: my_sinatra.tar
        push: True
    
    - name: Build image and with buildargs
       docker_image:
         path: /path/to/build/dir
         name: myimage
         buildargs:
           log_volume: /var/log/myapp
           listen_port: 8080

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
        <td> image </td>
        <td> Image inspection results for the affected image. </td>
        <td align=center> success </td>
        <td align=center> complex </td>
        <td align=center> {} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Connect to the Docker daemon by providing parameters with each task or by defining environment variables. You can define DOCKER_HOST, DOCKER_TLS_HOSTNAME, DOCKER_API_VERSION, DOCKER_CERT_PATH, DOCKER_SSL_VERSION, DOCKER_TLS, DOCKER_TLS_VERIFY and DOCKER_TIMEOUT. If you are using docker machine, run the script shipped with the product that sets up the environment. It will set these variables for you. See https://docker-py.readthedocs.org/en/stable/machine/ for more details.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

