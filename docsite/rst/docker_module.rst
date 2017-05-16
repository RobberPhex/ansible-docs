.. _docker:


docker - manage docker containers
+++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This is the original Ansible module for managing the Docker container life cycle.
NOTE: Additional and newer modules are available. For the latest on orchestrating containers with Ansible visit our Getting Started with Docker Guide at https://github.com/ansible/ansible/blob/devel/docsite/rst/guide_docker.rst.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * docker-py >= 0.3.0
  * The docker server >= 0.10.0


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
    <td>cap_add<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Add capabilities for the container. Requires docker-py &gt;= 0.5.0.</div></td></tr>
            <tr>
    <td>cap_drop<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Drop capabilities for the container. Requires docker-py &gt;= 0.5.0.</div></td></tr>
            <tr>
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Command used to match and launch containers.</div></td></tr>
            <tr>
    <td>count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>Number of matching containers that should be in the desired state.</div></td></tr>
            <tr>
    <td>cpu_set<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>CPUs in which to allow execution. Requires docker-py &gt;= 0.6.0.</div></td></tr>
            <tr>
    <td>cpu_shares<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>CPU shares (relative weight). Requires docker-py &gt;= 0.6.0.</div></td></tr>
            <tr>
    <td>detach<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Enable detached mode to leave the container running in background. If disabled, fail unless the process exits cleanly.</div></td></tr>
            <tr>
    <td>devices<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of host devices to expose to container</div></td></tr>
            <tr>
    <td>dns<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of custom DNS servers for the container.</div></td></tr>
            <tr>
    <td>docker_api_version<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>docker-py default remote API version</td>
        <td><ul></ul></td>
        <td><div>Remote API version to use. This defaults to the current default as specified by docker-py.</div></td></tr>
            <tr>
    <td>docker_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>${DOCKER_HOST} or unix://var/run/docker.sock</td>
        <td><ul></ul></td>
        <td><div>URL of the host running the docker daemon. This will default to the env var DOCKER_HOST if unspecified.</div></td></tr>
            <tr>
    <td>docker_user<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username or UID to use within the container</div></td></tr>
            <tr>
    <td>domainname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Container domain name.</div></td></tr>
            <tr>
    <td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Remote API email.</div></td></tr>
            <tr>
    <td>entrypoint<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Corresponds to ``--entrypoint`` option of ``docker run`` command and ``ENTRYPOINT`` directive of Dockerfile. Used to match and launch containers.</div></td></tr>
            <tr>
    <td>env<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Pass a dict of environment variables to the container.</div></td></tr>
            <tr>
    <td>env_file<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Pass in a path to a file with environment variable (FOO=BAR). If a key value is present in both explicitly presented (i.e. as 'env') and in the environment file, the explicit value will override. Requires docker-py &gt;= 1.4.0.</div></td></tr>
            <tr>
    <td>expose<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of additional container ports to expose for port mappings or links. If the port is already exposed using EXPOSE in a Dockerfile, you don't need to expose it again.</div></td></tr>
            <tr>
    <td>extra_hosts<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dict of custom host-to-IP mappings to be defined in the container</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Container hostname.</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Container image used to match and launch containers.</div></td></tr>
            <tr>
    <td>insecure_registry<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use insecure private registry by HTTP instead of HTTPS. Needed for docker-py &gt;= 0.5.0.</div></td></tr>
            <tr>
    <td>labels<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set container labels. Requires docker &gt;= 1.6 and docker-py &gt;= 1.2.0.</div></td></tr>
            <tr>
    <td>links<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of other containers to link within this container with an optional</div><div>alias. Use docker CLI-style syntax: <code>redis:myredis</code>.</div></td></tr>
            <tr>
    <td>log_driver<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>json-file</td>
        <td><ul><li>json-file</li><li>none</li><li>syslog</li><li>journald</li><li>gelf</li><li>fluentd</li><li>awslogs</li></ul></td>
        <td><div>You can specify a different logging driver for the container than for the daemon. "json-file" Default logging driver for Docker. Writes JSON messages to file. docker logs command is available only for this logging driver. "none" disables any logging for the container. "syslog" Syslog logging driver for Docker. Writes log messages to syslog. docker logs command is not available for this logging driver. "journald" Journald logging driver for Docker. Writes log messages to "journald". "gelf" Graylog Extended Log Format (GELF) logging driver for Docker. Writes log messages to a GELF endpoint likeGraylog or Logstash. "fluentd" Fluentd logging driver for Docker. Writes log messages to "fluentd" (forward input). "awslogs" (added in 2.1) Awslogs logging driver for Docker. Writes log messages to AWS Cloudwatch Logs. If not defined explicitly, the Docker daemon's default ("json-file") will apply. Requires docker &gt;= 1.6.0.</div></td></tr>
            <tr>
    <td>log_opt<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Additional options to pass to the logging driver selected above. See Docker `log-driver &lt;https://docs.docker.com/reference/logging/overview/&gt;` documentation for more information. Requires docker &gt;=1.7.0.</div></td></tr>
            <tr>
    <td>lxc_conf<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>LXC configuration parameters, such as <code>lxc.aa_profile:unconfined</code>.</div></td></tr>
            <tr>
    <td>memory_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>RAM allocated to the container as a number of bytes or as a human-readable string like "512MB". Leave as "0" to specify no limit.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name used to match and uniquely name launched containers. Explicit names are used to uniquely identify a single container or to link among containers. Mutually exclusive with a "count" other than "1".</div></td></tr>
            <tr>
    <td>net<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Network mode for the launched container: bridge, none, container:&lt;name|id&gt;</div><div>or host. Requires docker &gt;= 0.11.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Remote API password.</div></td></tr>
            <tr>
    <td>pid<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Set the PID namespace mode for the container (currently only supports 'host'). Requires docker-py &gt;= 1.0.0 and docker &gt;= 1.5.0</div></td></tr>
            <tr>
    <td>ports<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List containing private to public port mapping specification. Use docker 'CLI-style syntax: <code>8000</code>, <code>9000:8000</code>, or <code>0.0.0.0:9000:8000</code>' where 8000 is a container port, 9000 is a host port, and 0.0.0.0 is - a host interface. The container ports need to be exposed either in the Dockerfile or via the <code>expose</code> option.</div></td></tr>
            <tr>
    <td>privileged<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether the container should run in privileged mode or not.</div></td></tr>
            <tr>
    <td>publish_all_ports<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Publish all exposed ports to the host interfaces.</div></td></tr>
            <tr>
    <td>pull<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>missing</td>
        <td><ul><li>missing</li><li>always</li></ul></td>
        <td><div>Control when container images are updated from the <code>docker_url</code> registry. If "missing," images will be pulled only when missing from the host; if '"always," the registry will be checked for a newer version of the image' each time the task executes.</div></td></tr>
            <tr>
    <td>read_only<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Mount the container's root filesystem as read only</div></td></tr>
            <tr>
    <td>registry<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>DockerHub</td>
        <td><ul></ul></td>
        <td><div>Remote registry URL to pull images from.</div></td></tr>
            <tr>
    <td>restart_policy<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>no</li><li>on-failure</li><li>always</li><li>unless-stopped</li></ul></td>
        <td><div>Container restart policy.</div><div>The 'unless-stopped' choice is only available starting in Ansible 2.1 and for Docker 1.9 and above.</div></td></tr>
            <tr>
    <td>restart_policy_retry<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Maximum number of times to restart a container. Leave as "0" for unlimited retries.</div></td></tr>
            <tr>
    <td>signal<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>KILL</td>
        <td><ul></ul></td>
        <td><div>With the state "killed", you can alter the signal sent to the container.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>present</li><li>started</li><li>reloaded</li><li>restarted</li><li>stopped</li><li>killed</li><li>absent</li></ul></td>
        <td><div>Assert the container's desired state. "present" only asserts that the matching containers exist. "started" asserts that the matching containers both exist and are running, but takes no action if any configuration has changed. "reloaded" (added in Ansible 1.9) asserts that all matching containers are running and restarts any that have any images or configuration out of date. "restarted" unconditionally restarts (or starts) the matching containers. "stopped" and '"killed" stop and kill all matching containers. "absent" stops and then' removes any matching containers.</div></td></tr>
            <tr>
    <td>stdin_open<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Keep stdin open after a container is launched.</div></td></tr>
            <tr>
    <td>stop_timeout<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>How many seconds to wait for the container to stop before killing it.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>60</td>
        <td><ul></ul></td>
        <td><div>Docker daemon response timeout in seconds.</div></td></tr>
            <tr>
    <td>tls_ca_cert<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>${DOCKER_CERT_PATH}/ca.pem</td>
        <td><ul></ul></td>
        <td><div>Path to a PEM-encoded certificate authority to secure the Docker connection. This has no effect if use_tls is encrypt.</div></td></tr>
            <tr>
    <td>tls_client_cert<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>${DOCKER_CERT_PATH}/cert.pem</td>
        <td><ul></ul></td>
        <td><div>Path to the PEM-encoded certificate used to authenticate docker client. If specified tls_client_key must be valid</div></td></tr>
            <tr>
    <td>tls_client_key<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>${DOCKER_CERT_PATH}/key.pem</td>
        <td><ul></ul></td>
        <td><div>Path to the PEM-encoded key used to authenticate docker client. If specified tls_client_cert must be valid</div></td></tr>
            <tr>
    <td>tls_hostname<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>Taken from docker_url</td>
        <td><ul></ul></td>
        <td><div>A hostname to check matches what's supplied in the docker server's certificate.  If unspecified, the hostname is taken from the docker_url.</div></td></tr>
            <tr>
    <td>tty<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Allocate a pseudo-tty within the container.</div></td></tr>
            <tr>
    <td>ulimits<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>ulimits, list ulimits with name, soft and optionally hard limit separated by colons. e.g. nofile:1024:2048 Requires docker-py &gt;= 1.2.0 and docker &gt;= 1.6.0</div></td></tr>
            <tr>
    <td>use_tls<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>no</li><li>encrypt</li><li>verify</li></ul></td>
        <td><div>Whether to use tls to connect to the docker server.  "no" means not to use tls (and ignore any other tls related parameters). "encrypt" means to use tls to encrypt the connection to the server.  "verify" means to also verify that the server's certificate is valid for the server (this both verifies the certificate against the CA and that the certificate was issued for that host. If this is unspecified, tls will only be used if one of the other tls options require it.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Remote API username.</div></td></tr>
            <tr>
    <td>volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of volumes to mount within the container</div><div>Use docker CLI-style syntax: <code>/host:/container[:mode]</code></div><div>You can specify a read mode for the mount with either <code>ro</code> or <code>rw</code>. Starting at version 2.1, SELinux hosts can additionally use <code>z</code> or <code>Z</code> mount options to use a shared or private label for the volume.</div></td></tr>
            <tr>
    <td>volumes_from<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of names of containers to mount volumes from.</div></td></tr>
        </table>
    </br>



Examples
--------

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
    # - grant the container read write permissions for the host's /dev/sda device
    #   through a node named /dev/xvda
    # - bind TCP port 9000 within the container to port 8080 on all interfaces
    #   on the host.
    # - bind UDP port 9001 within the container to port 8081 on the host, only
    #   listening on localhost.
    # - specify 2 ip resolutions.
    # - set the environment variable SECRET_KEY to "ssssh".
    
    - name: application container
      docker:
        name: myapplication
        image: someuser/appimage
        state: reloaded
        pull: always
        links:
        - "myredis:aliasedredis"
        devices:
        - "/dev/sda:/dev/xvda:rwm"
        ports:
        - "8080:9000"
        - "127.0.0.1:8081:9001/udp"
        extra_hosts:
          host1: "192.168.0.1"
          host2: "192.168.0.2"
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
    
    # Example Syslogging Output
    
    - name: myservice container
      docker:
        name: myservice
        image: someservice/someimage
        state: reloaded
        log_driver: syslog
        log_opt:
          syslog-address: tcp://my-syslog-server:514
          syslog-facility: daemon
          syslog-tag: myservice




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

