.. _docker_service:


docker_service - Manage docker services and containers.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Consumes docker compose to start, shutdown and scale services.
Works with compose versions 1 and 2.
Compose can be read from a docker-compose.yml (or .yaml) file or inline using the ``definition`` option.
See the examples for more details.
Supports check mode.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * docker-compose >= 1.7.0
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
    <td>build<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to build images before starting containers.</div><div>Missing images will always be built.</div><div>If an image is present and <code>build</code> is false, the image will not be built.</div><div>If an image is present and <code>build</code> is true, the image will be built.</div></td></tr>
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
    <td>debug<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Include <em>actions</em> in the return values.</div></td></tr>
            <tr>
    <td>definition<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide docker-compose yaml describing one or more services, networks and volumes.</div><div>Mutually exclusive with <code>project_src</code> and <code>project_files</code>.</div></td></tr>
            <tr>
    <td>dependencies<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When <code>state</code> is <em>present</em> specify whether or not to include linked services.</div></td></tr>
            <tr>
    <td>docker_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>unix://var/run/docker.sock</td>
        <td><ul></ul></td>
        <td><div>The URL or Unix socket path used to connect to the Docker API. To connect to a remote host, provide the TCP connection string. For example, 'tcp://192.168.99.100:2376'. If TLS is used to encrypt the connection, the module will automatically replace 'tcp' in the connection URL with 'https'.</div></br>
        <div style="font-size: small;">aliases: docker_url<div></td></tr>
            <tr>
    <td>files<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of file names relative to <code>project_src</code>. Overrides docker-compose.yml or docker-compose.yaml.</div><div>Files are loaded and merged in the order given.</div></td></tr>
            <tr>
    <td>hostname_check<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to check the Docker daemon's hostname against the name provided in the client certificate.</div></td></tr>
            <tr>
    <td>key_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the client's TLS key file.</div></br>
        <div style="font-size: small;">aliases: tls_client_key<div></td></tr>
            <tr>
    <td>project_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide a project name. If not provided, the project name is taken from the basename of <code>project_src</code>.</div><div>Required when no <code>definition</code> is provided.</div></td></tr>
            <tr>
    <td>project_src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to a directory containing a docker-compose.yml or docker-compose.yaml file.</div><div>Mutually exclusive with <code>definition</code>.</div><div>Required when no <code>definition</code> is provided.</div></td></tr>
            <tr>
    <td>recreate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>smart</td>
        <td><ul><li>always</li><li>never</li><li>smart</li></ul></td>
        <td><div>By default containers will be recreated when their configuration differs from the service definition.</div><div>Setting to <em>never</em> ignores configuration differences and leaves existing containers unchanged.</div><div>Setting to <em>always</em> forces recreation of all existing containers.</div></td></tr>
            <tr>
    <td>remove_images<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with state <em>absent</em> to remove the all images or only local images.</div></td></tr>
            <tr>
    <td>remove_volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Use with state <em>absent</em> to remove data volumes.</div></td></tr>
            <tr>
    <td>restarted<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Use with state <em>present</em> to restart all containers.</div></td></tr>
            <tr>
    <td>scale<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When <code>sate</code> is <em>present</em> scale services. Provide a dictionary of key/value pairs where the key is the name of the service and the value is an integer count for the number of containers.</div></td></tr>
            <tr>
    <td>services<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When <code>state</code> is <em>present</em> run <em>docker-compose up</em> on a subset of services.</div></td></tr>
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
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Desired state of the project.</div><div>Specifying <em>present</em> is the same as running <em>docker-compose up</em>.</div><div>Specifying <em>absent</em> is the same as running <em>docker-compose down</em>.</div></td></tr>
            <tr>
    <td>stopped<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Use with state <em>present</em> to leave the containers in an exited or non-running state.</div></td></tr>
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
        </table>
    </br>



Examples
--------

 ::

    # Examples use the django example at U(https://docs.docker.com/compose/django/). Follow it to create the flask
    # directory
    
    - name: Run using a project directory
      hosts: localhost
      connection: local
      gather_facts: no
      tasks:
        - docker_service:
            project_src: flask
            state: absent
    
        - docker_service:
            project_src: flask
          register: output
    
        - debug: var=output
    
        - docker_service:
            project_src: flask
            build: no
          register: output
    
        - debug: var=output
    
        - assert:
            that: "not output.changed "
    
        - docker_service:
            project_src: flask
            build: no
            stopped: true
          register: output
    
        - debug: var=output
    
        - assert:
            that:
              - "not web.flask_web_1.state.running"
              - "not db.flask_db_1.state.running"
    
        - docker_service:
            project_src: flask
            build: no
            restarted: true
          register: output
    
        - debug: var=output
    
        - assert:
            that:
              - "web.flask_web_1.state.running"
              - "db.flask_db_1.state.running"
    
    - name: Scale the web service to 2
      hosts: localhost
      connection: local
      gather_facts: no
      tasks:
        - docker_service:
            project_src: flask
            scale:
              web: 2
          register: output
    
        - debug: var=output
    
    - name: Run with inline v2 compose
      hosts: localhost
      connection: local
      gather_facts: no
      tasks:
        - docker_service:
            project_src: flask
            state: absent
    
        - docker_service:
            project_name: flask
            definition:
              version: '2'
              services:
                db:
                  image: postgres
                web:
                  build: "{{ playbook_dir }}/flask"
                  command: "python manage.py runserver 0.0.0.0:8000"
                  volumes:
                    - "{{ playbook_dir }}/flask:/code"
                  ports:
                    - "8000:8000"
                  depends_on:
                    - db
          register: output
    
        - debug: var=output
    
        - assert:
            that:
              - "web.flask_web_1.state.running"
              - "db.flask_db_1.state.running"
    
    - name: Run with inline v1 compose
      hosts: localhost
      connection: local
      gather_facts: no
      tasks:
        - docker_service:
            project_src: flask
            state: absent
    
        - docker_service:
            project_name: flask
            definition:
                db:
                  image: postgres
                web:
                  build: "{{ playbook_dir }}/flask"
                  command: "python manage.py runserver 0.0.0.0:8000"
                  volumes:
                    - "{{ playbook_dir }}/flask:/code"
                  ports:
                    - "8000:8000"
                  links:
                    - db
          register: output
    
        - debug: var=output
    
        - assert:
            that:
              - "web.flask_web_1.state.running"
              - "db.flask_db_1.state.running"

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
        <td> service </td>
        <td> Name of the service. </td>
        <td align=center> success </td>
        <td align=center> complex </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> actions </td>
        <td> Provides the actions to be taken on each service as determined by compose. </td>
        <td align=center> when in check mode or I(debug) true </td>
        <td align=center> complex </td>
        <td align=center>  </td>
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

