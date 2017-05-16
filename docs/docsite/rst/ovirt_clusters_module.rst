.. _ovirt_clusters:


ovirt_clusters - Module to manage clusters in oVirt
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Module to manage clusters in oVirt


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * ovirt-engine-sdk-python >= 4.0.0


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
                <tr><td>auth<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values needed to create HTTP/HTTPS connection to oVirt:</div><div><code>username</code>[<em>required</em>] - The name of the user, something like <em>admin@internal</em>. Default value is set by <em>OVIRT_USERNAME</em> environment variable.</div><div><code>password</code>[<em>required</em>] - The password of the user. Default value is set by <em>OVIRT_PASSWORD</em> environment variable.</div><div><code>url</code>[<em>required</em>] - A string containing the base URL of the server, usually something like `<em>https://server.example.com/ovirt-engine/api</em>`. Default value is set by <em>OVIRT_URL</em> environment variable.</div><div><code>token</code> - Token to be used instead of login with username/password. Default value is set by <em>OVIRT_TOKEN</em> environment variable.</div><div><code>insecure</code> - A boolean flag that indicates if the server TLS certificate and host name should be checked.</div><div><code>ca_file</code> - A PEM file containing the trusted CA certificates. The certificate presented by the server will be verified using these CA certificates. If `<code>ca_file</code>` parameter is not set, system wide CA certificate store is used. Default value is set by <em>OVIRT_CAFILE</em> environment variable.</div><div><code>kerberos</code> - A boolean flag indicating if Kerberos authentication should be used instead of the default basic authentication.</div>        </td></tr>
                <tr><td>ballooning<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> enable memory balloon optimization. Memory balloon is used to re-distribute / reclaim the host memory based on VM needs in a dynamic way.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Comment of the cluster.</div>        </td></tr>
                <tr><td>compatibility_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The compatibility version of the cluster. All hosts in this cluster must support at least this compatibility version.</div>        </td></tr>
                <tr><td>cpu_arch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>x86_64</li><li>ppc64</li><li>undefined</li></ul></td>
        <td><div>CPU architecture of cluster.</div>        </td></tr>
                <tr><td>cpu_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>CPU codename. For example <em>Intel SandyBridge Family</em>.</div>        </td></tr>
                <tr><td>data_center<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Datacenter name where cluster reside.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of the cluster.</div>        </td></tr>
                <tr><td>fence_connectivity_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The threshold used by <code>fence_skip_if_connectivity_broken</code>.</div>        </td></tr>
                <tr><td>fence_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> enables fencing on the cluster.</div><div>Fencing is enabled by default.</div>        </td></tr>
                <tr><td>fence_skip_if_connectivity_broken<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> fencing will be temporarily disabled if the percentage of hosts in the cluster that are experiencing connectivity issues is greater than or equal to the defined threshold.</div><div>The threshold can be specified by <code>fence_connectivity_threshold</code>.</div>        </td></tr>
                <tr><td>fence_skip_if_sd_active<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> any hosts in the cluster that are Non Responsive and still connected to storage will not be fenced.</div>        </td></tr>
                <tr><td>fetch_nested<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> the module will fetch additional data from the API.</div><div>It will fetch IDs of the VMs disks, snapshots, etc. User can configure to fetch other attributes of the nested entities by specifying <code>nested_attributes</code>.</div>        </td></tr>
                <tr><td>gluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em>, hosts in this cluster will be used as Gluster Storage server nodes, and not for running virtual machines.</div><div>By default the cluster is created for virtual machine hosts.</div>        </td></tr>
                <tr><td>ha_reservation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> enable the oVirt to monitor cluster capacity for highly available virtual machines.</div>        </td></tr>
                <tr><td>host_reason<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> enable an optional reason field when a host is placed into maintenance mode from the Manager, allowing the administrator to provide an explanation for the maintenance.</div>        </td></tr>
                <tr><td>ksm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>I <em>True</em> MoM enables to run Kernel Same-page Merging <em>KSM</em> when necessary and when it can yield a memory saving benefit that outweighs its CPU cost.</div>        </td></tr>
                <tr><td>ksm_numa<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> enables KSM <code>ksm</code> for best berformance inside NUMA nodes.</div>        </td></tr>
                <tr><td>memory_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>disabled</li><li>server</li><li>desktop</li></ul></td>
        <td><div><em>disabled</em> - Disables memory page sharing.</div><div><em>server</em> - Sets the memory page sharing threshold to 150% of the system memory on each host.</div><div><em>desktop</em> - Sets the memory page sharing threshold to 200% of the system memory on each host.</div>        </td></tr>
                <tr><td>migration_auto_converge<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li><li>inherit</li></ul></td>
        <td><div>If <em>True</em> auto-convergence is used during live migration of virtual machines.</div><div>Used only when <code>migration_policy</code> is set to <em>legacy</em>.</div><div>Following options are supported:</div><div><code>true</code> - Override the global setting to <em>true</em>.</div><div><code>false</code> - Override the global setting to <em>false</em>.</div><div><code>inherit</code> - Use value which is set globally.</div>        </td></tr>
                <tr><td>migration_bandwidth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>auto</li><li>hypervisor_default</li><li>custom</li></ul></td>
        <td><div>The bandwidth settings define the maximum bandwidth of both outgoing and incoming migrations per host.</div><div>Following bandwith options are supported:</div><div><code>auto</code> - Bandwidth is copied from the <em>rate limit</em> [Mbps] setting in the data center host network QoS.</div><div><code>hypervisor_default</code> - Bandwidth is controlled by local VDSM setting on sending host.</div><div><code>custom</code> - Defined by user (in Mbps).</div>        </td></tr>
                <tr><td>migration_bandwidth_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set the <em>custom</em> migration bandwidth limit.</div><div>This parameter is used only when <code>migration_bandwidth</code> is <em>custom</em>.</div>        </td></tr>
                <tr><td>migration_compressed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li><li>inherit</li></ul></td>
        <td><div>If <em>True</em> compression is used during live migration of the virtual machine.</div><div>Used only when <code>migration_policy</code> is set to <em>legacy</em>.</div><div>Following options are supported:</div><div><code>true</code> - Override the global setting to <em>true</em>.</div><div><code>false</code> - Override the global setting to <em>false</em>.</div><div><code>inherit</code> - Use value which is set globally.</div>        </td></tr>
                <tr><td>migration_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>legacy</li><li>minimal_downtime</li><li>suspend_workload</li></ul></td>
        <td><div>A migration policy defines the conditions for live migrating virtual machines in the event of host failure.</div><div>Following policies are supported:</div><div><code>legacy</code> - Legacy behavior of 3.6 version.</div><div><code>minimal_downtime</code> - Virtual machines should not experience any significant downtime.</div><div><code>suspend_workload</code> - Virtual machines may experience a more significant downtime.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the the cluster to manage.</div>        </td></tr>
                <tr><td>nested_attributes<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies list of the attributes which should be fetched from the API.</div><div>This parameter apply only when <code>fetch_nested</code> is <em>true</em>.</div>        </td></tr>
                <tr><td>network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Management network of cluster to access cluster hosts.</div>        </td></tr>
                <tr><td>poll_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3</td>
        <td></td>
        <td><div>Number of the seconds the module waits until another poll request on entity status is sent.</div>        </td></tr>
                <tr><td>resilience_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>do_not_migrate</li><li>migrate</li><li>migrate_highly_available</li></ul></td>
        <td><div>The resilience policy defines how the virtual machines are prioritized in the migration.</div><div>Following values are supported:</div><div><code>do_not_migrate</code> -  Prevents virtual machines from being migrated. </div><div><code>migrate</code> - Migrates all virtual machines in order of their defined priority.</div><div><code>migrate_highly_available</code> - Migrates only highly available virtual machines to prevent overloading other hosts.</div>        </td></tr>
                <tr><td>rng_sources<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List that specify the random number generator devices that all hosts in the cluster will use.</div><div>Supported generators are: <em>hwrng</em> and <em>random</em>.</div>        </td></tr>
                <tr><td>scheduling_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the scheduling policy to be used for cluster.</div>        </td></tr>
                <tr><td>serial_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a serial number policy for the virtual machines in the cluster.</div><div>Following options are supported:</div><div><code>vm</code> - Sets the virtual machine's UUID as its serial number.</div><div><code>host</code> - Sets the host's UUID as the virtual machine's serial number.</div><div><code>custom</code> - Allows you to specify a custom serial number in <code>serial_policy_value</code>.</div>        </td></tr>
                <tr><td>serial_policy_value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Allows you to specify a custom serial number.</div><div>This parameter is used only when <code>serial_policy</code> is <em>custom</em>.</div>        </td></tr>
                <tr><td>spice_proxy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The proxy by which the SPICE client will connect to virtual machines.</div><div>The address must be in the following format: <em>protocol://[host]:[port]</em></div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Should the cluster be present or absent</div>        </td></tr>
                <tr><td>switch_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>legacy</li><li>ovs</li></ul></td>
        <td><div>Type of switch to be used by all networks in given cluster. Either <em>legacy</em> which is using linux brigde or <em>ovs</em> using Open vSwitch.</div>        </td></tr>
                <tr><td>threads_as_cores<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> the exposed host threads would be treated as cores which can be utilized by virtual machines.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td></td>
        <td><div>The amount of time in seconds the module should wait for the instance to get into desired state.</div>        </td></tr>
                <tr><td>trusted_service<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If (True) enable integration with an OpenAttestation server.</div>        </td></tr>
                <tr><td>virt<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em>, hosts in this cluster will be used to run virtual machines.</div>        </td></tr>
                <tr><td>vm_reason<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> enable an optional reason field when a virtual machine is shut down from the Manager, allowing the administrator to provide an explanation for the maintenance.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div><em>True</em> if the module should wait for the entity to get into desired state.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Examples don't contain auth parameter for simplicity,
    # look at ovirt_auth module to see how to reuse authentication:
    
    # Create cluster
    - ovirt_clusters:
        data_center: mydatacenter
        name: mycluster
        cpu_type: Intel SandyBridge Family
        description: mycluster
        compatibility_version: 4.0
    
    # Create virt service cluster:
    - ovirt_clusters:
        data_center: mydatacenter
        name: mycluster
        cpu_type: Intel Nehalem Family
        description: mycluster
        switch_type: legacy
        compatibility_version: 4.0
        ballooning: true
        gluster: false
        threads_as_cores: true
        ha_reservation: true
        trusted_service: false
        host_reason: false
        vm_reason: true
        ksm_numa: true
        memory_policy: server
        rng_sources:
          - hwrng
          - random
    
    # Remove cluster
    - ovirt_clusters:
        state: absent
        name: mycluster

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
        <td> cluster </td>
        <td> Dictionary of all the cluster attributes. Cluster attributes can be found on your oVirt instance at following url: https://ovirt.example.com/ovirt-engine/api/model#types/cluster. </td>
        <td align=center> On success if cluster is found. </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> id </td>
        <td> ID of the cluster which is managed </td>
        <td align=center> On success if cluster is found. </td>
        <td align=center> str </td>
        <td align=center> 7de90f31-222c-436c-a1ca-7e655bd5b60c </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - In order to use this module you have to install oVirt Python SDK. To ensure it's installed with correct version you can create the following task: *pip: name=ovirt-engine-sdk-python version=4.0.0*



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
