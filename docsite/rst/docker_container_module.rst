.. _docker_container:


docker_container - manage docker containers
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage the life cycle of docker containers.
Supports check mode. Run with --check and --diff to view config difference and list of actions to be taken.


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
    <td>blkio_weight<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Block IO (relative weight), between 10 and 1000.</div></td></tr>
            <tr>
    <td>cacert_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use a CA certificate when performing server verification by providing the path to a CA certificate file.</div></br>
        <div style="font-size: small;">aliases: tls_ca_cert<div></td></tr>
            <tr>
    <td>capabilities<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of capabilities to add to the container.</div></td></tr>
            <tr>
    <td>cert_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the client's TLS certificate file.</div></br>
        <div style="font-size: small;">aliases: tls_client_cert<div></td></tr>
            <tr>
    <td>cleanup<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with <em>detach</em> to remove the container after successful execution.</div></td></tr>
            <tr>
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Command to execute when the container starts.</div></td></tr>
            <tr>
    <td>cpu_period<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Limit CPU CFS (Completely Fair Scheduler) period</div></td></tr>
            <tr>
    <td>cpu_quota<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Limit CPU CFS (Completely Fair Scheduler) quota</div></td></tr>
            <tr>
    <td>cpu_shares<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>CPU shares (relative weight).</div></td></tr>
            <tr>
    <td>cpuset_cpus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>CPUs in which to allow execution <code>1,3</code> or <code>1-3</code>.</div></td></tr>
            <tr>
    <td>cpuset_mems<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Memory nodes (MEMs) in which to allow execution <code>0-3</code> or <code>0,1</code></div></td></tr>
            <tr>
    <td>detach<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Enable detached mode to leave the container running in background. If disabled, the task will reflect the status of the container run (failed if the command failed).</div></td></tr>
            <tr>
    <td>devices<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of host device bindings to add to the container. Each binding is a mapping expressed in the format: &lt;path_on_host&gt;:&lt;path_in_container&gt;:&lt;cgroup_permissions&gt;</div></td></tr>
            <tr>
    <td>dns_search_domains<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of custom DNS search domains.</div></td></tr>
            <tr>
    <td>dns_servers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of custom DNS servers.</div></td></tr>
            <tr>
    <td>docker_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>unix://var/run/docker.sock</td>
        <td><ul></ul></td>
        <td><div>The URL or Unix socket path used to connect to the Docker API. To connect to a remote host, provide the TCP connection string. For example, 'tcp://192.0.2.23:2376'. If TLS is used to encrypt the connection, the module will automatically replace 'tcp' in the connection URL with 'https'.</div></br>
        <div style="font-size: small;">aliases: docker_url<div></td></tr>
            <tr>
    <td>entrypoint<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Command that overwrites the default ENTRYPOINT of the image.</div></td></tr>
            <tr>
    <td>env<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary of key,value pairs.</div></td></tr>
            <tr>
    <td>env_file<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to a file containing environment variables <em>FOO=BAR</em>.</div><div>If variable also present in <code>env</code>, then <code>env</code> value will override.</div><div>Requires docker-py &gt;= 1.4.0.</div></td></tr>
            <tr>
    <td>etc_hosts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dict of host-to-IP mappings, where each host name is a key in the dictionary. Each host name will be added to the container's /etc/hosts file.</div></td></tr>
            <tr>
    <td>exposed_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of additional container ports which informs Docker that the container listens on the specified network ports at runtime. If the port is already exposed using EXPOSE in a Dockerfile, it does not need to be exposed again.</div></br>
        <div style="font-size: small;">aliases: exposed<div></td></tr>
            <tr>
    <td>force_kill<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use the kill command when stopping a running container.</div></td></tr>
            <tr>
    <td>groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of additional group names and/or IDs that the container process will run as.</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Container hostname.</div></td></tr>
            <tr>
    <td>ignore_image<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When <code>state</code> is <em>present</em> or <em>started</em> the module compares the configuration of an existing container to requested configuration. The evaluation includes the image version. If the image version in the registry does not match the container, the container will be recreated. Stop this behavior by setting <code>ignore_image</code> to <em>True</em>.</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Repository path and tag used to create the container. If an image is not found or pull is true, the image will be pulled from the registry. If no tag is included, 'latest' will be used.</div></td></tr>
            <tr>
    <td>interactive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Keep stdin open after a container is launched, even if not attached.</div></td></tr>
            <tr>
    <td>ipc_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the IPC mode for the container. Can be one of 'container:&lt;name|id&gt;' to reuse another container's IPC namespace or 'host' to use the host's IPC namespace within the container.</div></td></tr>
            <tr>
    <td>keep_volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Retain volumes associated with a removed container.</div></td></tr>
            <tr>
    <td>kernel_memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Kernel memory limit (format: &lt;number&gt;[&lt;unit&gt;]). Number is a positive integer. Unit can be one of b, k, m, or g. Minimum is 4M.</div></td></tr>
            <tr>
    <td>key_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the client's TLS key file.</div></br>
        <div style="font-size: small;">aliases: tls_client_key<div></td></tr>
            <tr>
    <td>kill_signal<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Override default signal used to kill a running container.</div></td></tr>
            <tr>
    <td>labels<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary of key value pairs.</div></td></tr>
            <tr>
    <td>links<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of name aliases for linked containers in the format <code>container_name:alias</code></div></td></tr>
            <tr>
    <td>log_driver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>json-file</li><li>syslog</li><li>journald</li><li>gelf</li><li>fluentd</li><li>awslogs</li><li>splunk</li></ul></td>
        <td><div>Specify the logging driver. Docker uses json-file by default.</div></td></tr>
            <tr>
    <td>log_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary of options specific to the chosen log_driver. See https://docs.docker.com/engine/admin/logging/overview/ for details.</div></td></tr>
            <tr>
    <td>mac_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Container MAC address (e.g. 92:d0:c6:0a:29:33)</div></td></tr>
            <tr>
    <td>memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Memory limit (format: &lt;number&gt;[&lt;unit&gt;]). Number is a positive integer. Unit can be one of b, k, m, or g</div></td></tr>
            <tr>
    <td>memory_reservation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Memory soft limit (format: &lt;number&gt;[&lt;unit&gt;]). Number is a positive integer. Unit can be one of b, k, m, or g</div></td></tr>
            <tr>
    <td>memory_swap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Total memory limit (memory + swap, format:&lt;number&gt;[&lt;unit&gt;]). Number is a positive integer. Unit can be one of b, k, m, or g.</div></td></tr>
            <tr>
    <td>memory_swappiness<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Tune a container's memory swappiness behavior. Accepts an integer between 0 and 100.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Assign a name to a new container or match an existing container.</div><div>When identifying an existing container name may be a name or a long or short container ID.</div></td></tr>
            <tr>
    <td>network_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>bridge</li><li>container:<name|id></li><li>host</li><li>none</li></ul></td>
        <td><div>Connect the container to a network.</div></td></tr>
            <tr>
    <td>networks<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of networks the container belongs to.</div><div>Each network is a dict with keys <code>name</code>, <code>ipv4_address</code>, <code>ipv6_address</code>, <code>links</code>, <code>aliases</code>.</div><div>For each network <code>name</code> is required, all other keys are optional.</div><div>If included, <code>links</code> or <code>aliases</code> are lists.</div><div>For examples of the data structure and usage see EXAMPLES below.</div><div>To remove a container from one or more networks, use the <code>purge_networks</code> option.</div></td></tr>
            <tr>
    <td>oom_killer<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether or not to disable OOM Killer for the container.</div></td></tr>
            <tr>
    <td>oom_score_adj<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An integer value containing the score given to the container in order to tune OOM killer preferences.</div></td></tr>
            <tr>
    <td>paused<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with the started state to pause running processes inside the container.</div></td></tr>
            <tr>
    <td>pid_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the PID namespace mode for the container. Currently only supports 'host'.</div></td></tr>
            <tr>
    <td>privileged<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Give extended privileges to the container.</div></td></tr>
            <tr>
    <td>published_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of ports to publish from the container to the host.</div><div>Use docker CLI syntax: <code>8000</code>, <code>9000:8000</code>, or <code>0.0.0.0:9000:8000</code>, where 8000 is a container port, 9000 is a host port, and 0.0.0.0 is a host interface.</div><div>Container ports must be exposed either in the Dockerfile or via the <code>expose</code> option.</div><div>A value of ALL will publish all exposed container ports to random host ports, ignoring any other mappings.</div><div>If <code>networks</code> parameter is provided, will inspect each network to see if there exists a bridge network with optional parameter com.docker.network.bridge.host_binding_ipv4. If such a network is found, then published ports where no host IP address is specified will be bound to the host IP pointed to by com.docker.network.bridge.host_binding_ipv4. Note that the first bridge network with a com.docker.network.bridge.host_binding_ipv4 value encountered in the list of <code>networks</code> is the one that will be used.</div></br>
        <div style="font-size: small;">aliases: ports<div></td></tr>
            <tr>
    <td>pull<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If true, always pull the latest version of an image. Otherwise, will only pull an image when missing.</div></td></tr>
            <tr>
    <td>purge_networks<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Remove the container from ALL networks not included in <code>networks</code> parameter.</div><div>Any default networks such as <em>bridge</em>, if not found in <code>networks</code>, will be removed as well.</div></td></tr>
            <tr>
    <td>read_only<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Mount the container's root file system as read-only.</div></td></tr>
            <tr>
    <td>recreate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with present and started states to force the re-creation of an existing container.</div></td></tr>
            <tr>
    <td>restart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with started state to force a matching container to be stopped and restarted.</div></td></tr>
            <tr>
    <td>restart_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>on-failure</td>
        <td><ul><li>always</li><li>False</li><li>on-failure</li><li>unless-stopped</li></ul></td>
        <td><div>Container restart policy. Place quotes around <em>no</em> option.</div></td></tr>
            <tr>
    <td>restart_retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use with restart policy to control maximum number of restart attempts.</div></td></tr>
            <tr>
    <td>security_opts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of security options in the form of <code>"label:user:User"</code></div></td></tr>
            <tr>
    <td>shm_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Size of `/dev/shm`. The format is `&lt;number&gt;&lt;unit&gt;`. `number` must be greater than `0`. Unit is optional and can be `b` (bytes), `k` (kilobytes), `m` (megabytes), or `g` (gigabytes).</div><div>Omitting the unit defaults to bytes. If you omit the size entirely, the system uses `64m`.</div></td></tr>
            <tr>
    <td>ssl_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1.0</td>
        <td><ul></ul></td>
        <td><div>Provide a valid SSL version number. Default value determined by docker-py, currently 1.0.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>absent</li><li>present</li><li>stopped</li><li>started</li></ul></td>
        <td><div><em>absent</em> - A container matching the specified name will be stopped and removed. Use force_kill to kill the container rather than stopping it. Use keep_volumes to retain volumes associated with the removed container.</div><div><em>present</em> - Asserts the existence of a container matching the name and any provided configuration parameters. If no container matches the name, a container will be created. If a container matches the name but the provided configuration does not match, the container will be updated, if it can be. If it cannot be updated, it will be removed and re-created with the requested config. Image version will be taken into account when comparing configuration. To ignore image version use the ignore_image option. Use the recreate option to force the re-creation of the matching container. Use force_kill to kill the container rather than stopping it. Use keep_volumes to retain volumes associated with a removed container.</div><div><em>started</em> - Asserts there is a running container matching the name and any provided configuration. If no container matches the name, a container will be created and started. If a container matching the name is found but the configuration does not match, the container will be updated, if it can be. If it cannot be updated, it will be removed and a new container will be created with the requested configuration and started. Image version will be taken into account when comparing configuration. To ignore image version use the ignore_image option. Use recreate to always re-create a matching container, even if it is running. Use restart to force a matching container to be stopped and restarted. Use force_kill to kill a container rather than stopping it. Use keep_volumes to retain volumes associated with a removed container.</div><div><em>stopped</em> - Asserts that the container is first <em>present</em>, and then if the container is running moves it to a stopped state. Use force_kill to kill a container rather than stopping it.</div></td></tr>
            <tr>
    <td>stop_signal<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Override default signal used to stop the container.</div></td></tr>
            <tr>
    <td>stop_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Number of seconds to wait for the container to stop before sending SIGKILL.</div></td></tr>
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
    <td>trust_image_content<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If true, skip image verification.</div></td></tr>
            <tr>
    <td>tty<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Allocate a psuedo-TTY.</div></td></tr>
            <tr>
    <td>ulimits<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of ulimit options. A ulimit is specified as <code>nofile:262144:262144</code></div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets the username or UID used and optionally the groupname or GID for the specified command.</div><div>Can be [ user | user:group | uid | uid:gid | user:gid | uid:group ]</div></td></tr>
            <tr>
    <td>uts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the UTS namespace mode for the container.</div></td></tr>
            <tr>
    <td>volume_driver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>The container volume driver.</div></td></tr>
            <tr>
    <td>volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of volumes to mount within the container.</div><div>Use docker CLI-style syntax: <code>/host:/container[:mode]</code></div><div>You can specify a read mode for the mount with either <code>ro</code> or <code>rw</code>.</div><div>SELinux hosts can additionally use <code>z</code> or <code>Z</code> to use a shared or private label for the volume.</div></td></tr>
            <tr>
    <td>volumes_from<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of container names or Ids to get volumes from.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a data container
      docker_container:
        name: mydata
        image: busybox
        volumes:
          - /data
    
    - name: Re-create a redis container
      docker_container:
        name: myredis
        image: redis
        command: redis-server --appendonly yes
        state: present
        recreate: yes
        exposed_ports:
          - 6379
        volumes_from:
          - mydata
    
    - name: Restart a container
      docker_container:
        name: myapplication
        image: someuser/appimage
        state: started
        restart: yes
        links:
         - "myredis:aliasedredis"
        devices:
         - "/dev/sda:/dev/xvda:rwm"
        ports:
         - "8080:9000"
         - "127.0.0.1:8081:9001/udp"
        env:
            SECRET_KEY: ssssh
    
    - name: Container present
      docker_container:
        name: mycontainer
        state: present
        image: ubuntu:14.04
        command: sleep infinity 
    
    - name: Stop a container
      docker_container:
        name: mycontainer
        state: stopped
    
    - name: Start 4 load-balanced containers
      docker_container:
        name: "container{{ item }}"
        recreate: yes
        image: someuser/anotherappimage
        command: sleep 1d
      with_sequence: count=4
    
    - name: remove container
      docker_container:
        name: ohno
        state: absent
    
    - name: Syslogging output
      docker_container:
        name: myservice
        image: busybox
        log_driver: syslog
        log_options:
          syslog-address: tcp://my-syslog-server:514
          syslog-facility: daemon
          syslog-tag: myservice
    
    - name: Create db container and connect to network
      docker_container:
        name: db_test
        image: "postgres:latest"
        networks:
          - name: "{{ docker_network_name }}"
    
    - name: Start container, connect to network and link
      docker_container:
        name: sleeper
        image: ubuntu:14.04
        networks:
          - name: TestingNet
            ipv4_address: "172.1.1.100"
            aliases:
              - sleepyzz
            links:
              - db_test:db
          - name: TestingNet2
    
    - name: Start a container with a command
      docker_container:
        name: sleepy
        image: ubuntu:14.04
        command: sleep infinity
    
    - name: Add container to networks
      docker_container:
        docker_container:
        name: sleepy
        networks:
          - name: TestingNet
            ipv4_address: 172.1.1.18
            links:
              - sleeper
          - name: TestingNet2
            ipv4_address: 172.1.10.20
    
    - name: Update network with aliases
      docker_container:
        name: sleepy
        networks:
          - name: TestingNet
            aliases:
              - sleepyz
              - zzzz
    
    - name: Remove container from one network
      docker_container:
        name: sleepy
        networks:
          - name: TestingNet2
        purge_networks: yes
    
    - name: Remove container from all networks
      docker_container:
        name: sleepy
        purge_networks: yes
    

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
        <td> ansible_docker_container </td>
        <td> ['Facts representing the current state of the container. Matches the docker inspection output.', 'Note that facts are not part of registered vars but accessible directly.', 'Empty if C(state) is I(absent)', 'If detached is I(False), will include Output attribute containing any output from container run.'] </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> { "AppArmorProfile": "", "Args": [], "Config": { "AttachStderr": false, "AttachStdin": false, "AttachStdout": false, "Cmd": [ "/usr/bin/supervisord" ], "Domainname": "", "Entrypoint": null, "Env": [ "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin" ], "ExposedPorts": { "443/tcp": {}, "80/tcp": {} }, "Hostname": "8e47bf643eb9", "Image": "lnmp_nginx:v1", "Labels": {}, "OnBuild": null, "OpenStdin": false, "StdinOnce": false, "Tty": false, "User": "", "Volumes": { "/tmp/lnmp/nginx-sites/logs/": {} }, ... } </td>
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

