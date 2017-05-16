.. _docker:


docker - manage docker containers
+++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Manage the life cycle of docker containers.

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
    <td>command</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Command used to match and launch containers.</td>
    </tr>
            <tr>
    <td>count</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>Number of matching containers that should be in the desired state.</td>
    </tr>
            <tr>
    <td>detach</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Enable detached mode to leave the container running in background.</td>
    </tr>
            <tr>
    <td>dns</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of custom DNS servers for the container.</td>
    </tr>
            <tr>
    <td>docker_api_version</td>
    <td>no</td>
    <td>docker-py default remote API version</td>
        <td><ul></ul></td>
        <td>Remote API version to use. This defaults to the current default as specified by docker-py. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>docker_url</td>
    <td>no</td>
    <td>${DOCKER_HOST} or unix://var/run/docker.sock</td>
        <td><ul></ul></td>
        <td>URL of the host running the docker daemon. This will default to the env var DOCKER_HOST if unspecified.</td>
    </tr>
            <tr>
    <td>domainname</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Container domain name.</td>
    </tr>
            <tr>
    <td>email</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Remote API email.</td>
    </tr>
            <tr>
    <td>env</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pass a dict of environment variables to the container.</td>
    </tr>
            <tr>
    <td>expose</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of additional container ports to expose for port mappings or links. If the port is already exposed using EXPOSE in a Dockerfile, you don't need to expose it again. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>hostname</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Container hostname.</td>
    </tr>
            <tr>
    <td>image</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Container image used to match and launch containers.</td>
    </tr>
            <tr>
    <td>insecure_registry</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Use insecure private registry by HTTP instead of HTTPS. Needed for docker-py &gt;= 0.5.0. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>links</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of other containers to link within this container with an optionalalias. Use docker CLI-style syntax: <code>redis:myredis</code>. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>lxc_conf</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>LXC configuration parameters, such as <code>lxc.aa_profile:unconfined</code>.</td>
    </tr>
            <tr>
    <td>memory_limit</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>RAM allocated to the container as a number of bytes or as a human-readable string like "512MB". Leave as "0" to specify no limit.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name used to match and uniquely name launched containers. Explicit names are used to uniquely identify a single container or to link among containers. Mutually exclusive with a "count" other than "1". (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>net</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Network mode for the launched container: bridge, none, container:&lt;name|id&gt;or host. Requires docker &gt;= 0.11. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Remote API password.</td>
    </tr>
            <tr>
    <td>pid</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Set the PID namespace mode for the container (currently only supports 'host'). Requires docker-py &gt;= 1.0.0 and docker &gt;= 1.5.0 (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>ports</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List containing private to public port mapping specification. Use dockerCLI-style syntax: <code>8000</code>, <code>9000:8000</code>, or <code>0.0.0.0:9000:8000</code>where  8000 is a container port, 9000 is a host port, and 0.0.0.0 isa host interface. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>privileged</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether the container should run in privileged mode or not.</td>
    </tr>
            <tr>
    <td>publish_all_ports</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Publish all exposed ports to the host interfaces. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>pull</td>
    <td>no</td>
    <td>missing</td>
        <td><ul><li>missing</li><li>always</li></ul></td>
        <td>Control when container images are updated from the <code>docker_url</code> registry. If "missing," images will be pulled only when missing from the host; if '"always," the registry will be checked for a newer version of the image' each time the task executes. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>registry</td>
    <td>no</td>
    <td>DockerHub</td>
        <td><ul></ul></td>
        <td>Remote registry URL to pull images from. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>restart_policy</td>
    <td>no</td>
    <td></td>
        <td><ul><li>no</li><li>on-failure</li><li>always</li></ul></td>
        <td>Container restart policy. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>restart_policy_retry</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Maximum number of times to restart a container. Leave as "0" for unlimited retries. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>present</li><li>started</li><li>reloaded</li><li>restarted</li><li>stopped</li><li>killed</li><li>absent</li></ul></td>
        <td>Assert the container's desired state. "present" only asserts that the matching containers exist. "started" asserts that the matching containers both exist and are running, but takes no action if any configuration has changed. "reloaded" asserts that all matching containers are running and restarts any that have any images or configuration out of date. "restarted" unconditionally restarts (or starts) the matching containers. "stopped" and '"killed" stop and kill all matching containers. "absent" stops and then' removes any matching containers.</td>
    </tr>
            <tr>
    <td>stdin_open</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Keep stdin open after a container is launched. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>tls_ca_cert</td>
    <td>no</td>
    <td>${DOCKER_CERT_PATH}/ca.pem</td>
        <td><ul></ul></td>
        <td>Path to a PEM-encoded certificate authority to secure the Docker connection. This has no effect if use_tls is encrypt. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>tls_client_cert</td>
    <td>no</td>
    <td>${DOCKER_CERT_PATH}/cert.pem</td>
        <td><ul></ul></td>
        <td>Path to the PEM-encoded certificate used to authenticate docker client. If specified tls_client_key must be valid (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>tls_client_key</td>
    <td>no</td>
    <td>${DOCKER_CERT_PATH}/key.pem</td>
        <td><ul></ul></td>
        <td>Path to the PEM-encoded key used to authenticate docker client. If specified tls_client_cert must be valid (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>tls_hostname</td>
    <td>no</td>
    <td>Taken from docker_url</td>
        <td><ul></ul></td>
        <td>A hostname to check matches what's supplied in the docker server's certificate.  If unspecified, the hostname is taken from the docker_url. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>tty</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Allocate a pseudo-tty within the container. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>use_tls</td>
    <td>no</td>
    <td></td>
        <td><ul><li>no</li><li>encrypt</li><li>verify</li></ul></td>
        <td>Whether to use tls to connect to the docker server.  "no" means not to use tls (and ignore any other tls related parameters). "encrypt" means to use tls to encrypt the connection to the server.  "verify" means to also verify that the server's certificate is valid for the server (this both verifies the certificate against the CA and that the certificate was issued for that host. If this is unspecified, tls will only be used if one of the other tls options require it. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Remote API username.</td>
    </tr>
            <tr>
    <td>volumes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of volumes to mount within the container using docker CLI-stylesyntax: <code>/host:/container[:mode]</code> where "mode" may be "rw" or "ro".</td>
    </tr>
            <tr>
    <td>volumes_from</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of names of containers to mount volumes from.</td>
    </tr>
        </table>


.. note:: Requires docker-py >= 0.3.0


.. note:: Requires docker >= 0.10.0


Examples
--------

.. raw:: html

    <br/>


::

    # Containers are matched either by name (if provided) or by an exact match of
    # the image they were launched with and the command they're running. The module
    # can accept either a name to target a container uniquely, or a count to operate
    # on multiple containers at once when it makes sense to do so.
    
    # Ensure that a data container with the name "mydata" exists. If no container
    # by this name exists, it will be created, but not started.
    
    - name: data container
      docker:
        name: mydata
        image: busybox
        state: present
        volumes:
        - /data
    
    # Ensure that a Redis server is running, using the volume from the data
    # container. Expose the default Redis port.
    
    - name: redis container
      docker:
        name: myredis
        image: redis
        command: redis-server --appendonly yes
        state: started
        expose:
        - 6379
        volumes_from:
        - mydata
    
    # Ensure that a container of your application server is running. This will:
    # - pull the latest version of your application image from DockerHub.
    # - ensure that a container is running with the specified name and exact image.
    #   If any configuration options have changed, the existing container will be
    #   stopped and removed, and a new one will be launched in its place.
    # - link this container to the existing redis container launched above with
    #   an alias.
    # - bind TCP port 9000 within the container to port 8080 on all interfaces
    #   on the host.
    # - bind UDP port 9001 within the container to port 8081 on the host, only
    #   listening on localhost.
    # - set the environment variable SECRET_KEY to "ssssh".
    
    - name: application container
      docker:
        name: myapplication
        image: someuser/appimage
        state: reloaded
        pull: always
        links:
        - "myredis:aliasedredis"
        ports:
        - "8080:9000"
        - "127.0.0.1:8081:9001/udp"
        env:
            SECRET_KEY: ssssh
    
    # Ensure that exactly five containers of another server are running with this
    # exact image and command. If fewer than five are running, more will be launched;
    # if more are running, the excess will be stopped.
    
    - name: load-balanced containers
      docker:
        state: reloaded
        count: 5
        image: someuser/anotherappimage
        command: sleep 1d
    
    # Unconditionally restart a service container. This may be useful within a
    # handler, for example.
    
    - name: application service
      docker:
        name: myservice
        image: someuser/serviceimage
        state: restarted
    
    # Stop all containers running the specified image.
    
    - name: obsolete container
      docker:
        image: someuser/oldandbusted
        state: stopped
    
    # Stop and remove a container with the specified name.
    
    - name: obsolete container
      docker:
        name: ohno
        image: someuser/oldandbusted
        state: absent



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

