.. _cs_host:


cs_host - Manages hosts on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update and remove hosts.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * cs >= 0.6.10


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
                <tr><td>allocation_state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>Allocation state of the host.</div>        </td></tr>
                <tr><td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div>        </td></tr>
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>API key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div>        </td></tr>
                <tr><td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secret key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>HTTP timeout.</div>        </td></tr>
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div>        </td></tr>
                <tr><td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the cluster.</div>        </td></tr>
                <tr><td>host_tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Tags of the host.</div>        </td></tr>
                <tr><td>hypervisor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>KVM</li><li>VMware</li><li>BareMetal</li><li>XenServer</li><li>LXC</li><li>HyperV</li><li>UCS</li><li>OVM</li><li>Simulator</li></ul></td>
        <td><div>Name of the cluster.</div><div>Required if <code>state=present</code> and host does not yet exist.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the host.</div></br>
    <div style="font-size: small;">aliases: url<div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password for the host.</div><div>Required if <code>state=present</code> and host does not yet exist.</div>        </td></tr>
                <tr><td>pod<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the pod.</div><div>Required if <code>state=present</code> and host does not yet exist.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the host.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username for the host.</div><div>Required if <code>state=present</code> and host does not yet exist.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the zone in which the host should be deployed.</div><div>If not set, default zone is used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a host is present but disabled
    - local_action:
        module: cs_host
        name: ix-pod01-esx01.example.com
        cluster: vcenter.example.com/ch-zrh-ix/pod01-cluster01
        pod: pod01
        zone: ch-zrh-ix-01
        hypervisor: VMware
        allocation_state: disabled
        host_tags:
        - perf
        - gpu
    
    # Ensure an existing host is disabled
    - local_action:
        module: cs_host
        name: ix-pod01-esx01.example.com
        zone: ch-zrh-ix-01
        allocation_state: disabled
    
    # Ensure an existing host is disabled
    - local_action:
        module: cs_host
        name: ix-pod01-esx01.example.com
        zone: ch-zrh-ix-01
        allocation_state: enabled
    
    # Ensure a host is absent
    - local_action:
        module: cs_host
        name: ix-pod01-esx01.example.com
        zone: ch-zrh-ix-01
        state: absent

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
        <td> network_kbs_write </td>
        <td> Outgoing network traffic on the host. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
    </tr>
            <tr>
        <td> cpu_allocated </td>
        <td> Amount in percent of the host's CPU currently allocated. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 166.25% </td>
    </tr>
            <tr>
        <td> host_tags </td>
        <td> Comma-separated list of tags for the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> perf </td>
    </tr>
            <tr>
        <td> is_local_storage_active </td>
        <td> Whether the local storage is available or not. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> cluster </td>
        <td> Cluster of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> vcenter.example.com/zone/cluster01 </td>
    </tr>
            <tr>
        <td> capabilities </td>
        <td> Capabilities of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> hvm </td>
    </tr>
            <tr>
        <td> cpu_speed </td>
        <td> CPU speed in Mhz </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 1999 </td>
    </tr>
            <tr>
        <td> cpu_used </td>
        <td> Amount of the host's CPU currently used. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 33.6% </td>
    </tr>
            <tr>
        <td> pod </td>
        <td> Pod name of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Pod01 </td>
    </tr>
            <tr>
        <td> cpu_sockets </td>
        <td> Number of CPU sockets of the host. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 2 </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Zone of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> zone01 </td>
    </tr>
            <tr>
        <td> cluster_type </td>
        <td> Type of the cluster of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ExternalManaged </td>
    </tr>
            <tr>
        <td> os_category </td>
        <td> OS category name of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ... </td>
    </tr>
            <tr>
        <td> management_server_id </td>
        <td> Management server ID of the host. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 345050593418 </td>
    </tr>
            <tr>
        <td> memory_total </td>
        <td> Total of memory of the host. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 206085263360 </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Up </td>
    </tr>
            <tr>
        <td> has_enough_capacity </td>
        <td> Whether the host has enough CPU and RAM capacity to migrate a VM to it. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> suitable_for_migration </td>
        <td> Whether this host is suitable (has enough capacity and satisfies all conditions like hosttags, max guests VM limit, etc) to migrate a VM to it or not. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> network_kbs_read </td>
        <td> Incoming network traffic on the host. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
    </tr>
            <tr>
        <td> events </td>
        <td> Events available for the host </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Ping; HostDown; AgentConnected; AgentDisconnected; PingTimeout; ShutdownRequested; Remove; StartAgentRebalance; ManagementServerDown </td>
    </tr>
            <tr>
        <td> host_version </td>
        <td> Version of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 4.5.2 </td>
    </tr>
            <tr>
        <td> memory_used </td>
        <td> Amount of the host's memory currently used. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 65504776192 </td>
    </tr>
            <tr>
        <td> last_pinged </td>
        <td> Date and time the host was last pinged. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1970-01-17T17:27:32+0100 </td>
    </tr>
            <tr>
        <td> disk_size_total </td>
        <td> Total disk size of the host </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 259300 </td>
    </tr>
            <tr>
        <td> gpu_group </td>
        <td> GPU cards present in the host. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [] </td>
    </tr>
            <tr>
        <td> cpu_with_overprovisioning </td>
        <td> Amount of the host's CPU after applying the cpu.overprovisioning.factor. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 959520.0 </td>
    </tr>
            <tr>
        <td> out_of_band_management </td>
        <td> Host out-of-band management information. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ... </td>
    </tr>
            <tr>
        <td> disk_size_allocated </td>
        <td> Host's currently allocated disk size. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 2593 </td>
    </tr>
            <tr>
        <td> removed </td>
        <td> Date and time the host was removed. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1970-01-17T17:27:32+0100 </td>
    </tr>
            <tr>
        <td> ip_address </td>
        <td> IP address of the host </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.10.10.1 </td>
    </tr>
            <tr>
        <td> disconnected </td>
        <td> Date when the host was disconnected. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2015-05-03T15:05:51+0200 </td>
    </tr>
            <tr>
        <td> cpu_number </td>
        <td> Number of CPUs of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 24 </td>
    </tr>
            <tr>
        <td> hypervisor_version </td>
        <td> Hypervisor version. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 5.1 </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> esx32.example.com </td>
    </tr>
            <tr>
        <td> created </td>
        <td> Date when the host was created. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2015-05-03T15:05:51+0200 </td>
    </tr>
            <tr>
        <td> hypervisor </td>
        <td> Host's hypervisor. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> VMware </td>
    </tr>
            <tr>
        <td> host_type </td>
        <td> Type of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Routing </td>
    </tr>
            <tr>
        <td> ha_host </td>
        <td> Whether the host is a HA host. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> memory_allocated </td>
        <td> Amount of the host's memory currently allocated. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 69793218560 </td>
    </tr>
            <tr>
        <td> resource_state </td>
        <td> Resource state of the host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Enabled </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
    - A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
    - This module supports check mode.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
