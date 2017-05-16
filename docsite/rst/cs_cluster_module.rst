.. _cs_cluster:


cs_cluster - Manages host clusters on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update and remove clusters.


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
            <tr>
    <td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div></td></tr>
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td><ul></ul></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div></td></tr>
            <tr>
    <td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Secret key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>HTTP timeout.</div></td></tr>
            <tr>
    <td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div></td></tr>
            <tr>
    <td>cluster_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>CloudManaged</li><li>ExternalManaged</li></ul></td>
        <td><div>Type of the cluster.</div><div>Required if <code>state=present</code></div></td></tr>
            <tr>
    <td>guest_vswitch_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of virtual switch used for guest traffic in the cluster.</div><div>This would override zone wide traffic label setting.</div></td></tr>
            <tr>
    <td>guest_vswitch_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>vmwaresvs</li><li>vmwaredvs</li></ul></td>
        <td><div>Type of virtual switch used for guest traffic in the cluster.</div><div>Allowed values are, vmwaresvs (for VMware standard vSwitch) and vmwaredvs (for VMware distributed vSwitch)</div></td></tr>
            <tr>
    <td>hypervisor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul><li>KVM</li><li>VMware</li><li>BareMetal</li><li>XenServer</li><li>LXC</li><li>HyperV</li><li>UCS</li><li>OVM</li></ul></td>
        <td><div>Name the hypervisor to be used.</div><div>Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the cluster.</div></td></tr>
            <tr>
    <td>ovm3_cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Ovm3 native OCFS2 clustering enabled for cluster.</div></td></tr>
            <tr>
    <td>ovm3_pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Ovm3 native pooling enabled for cluster.</div></td></tr>
            <tr>
    <td>ovm3_vip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Ovm3 vip to use for pool (and cluster).</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password for the cluster.</div></td></tr>
            <tr>
    <td>pod<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the pod in which the cluster belongs to.</div></td></tr>
            <tr>
    <td>public_vswitch_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of virtual switch used for public traffic in the cluster.</div><div>This would override zone wide traffic label setting.</div></td></tr>
            <tr>
    <td>public_vswitch_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>vmwaresvs</li><li>vmwaredvs</li></ul></td>
        <td><div>Type of virtual switch used for public traffic in the cluster.</div><div>Allowed values are, vmwaresvs (for VMware standard vSwitch) and vmwaredvs (for VMware distributed vSwitch)</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>disabled</li><li>enabled</li></ul></td>
        <td><div>State of the cluster.</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL for the cluster</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username for the cluster.</div></td></tr>
            <tr>
    <td>vms_ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>IP address of the VSM associated with this cluster.</div></td></tr>
            <tr>
    <td>vms_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password for the VSM associated with this cluster.</div></td></tr>
            <tr>
    <td>vms_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username for the VSM associated with this cluster.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the zone in which the cluster belongs to.</div><div>If not set, default zone is used.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a cluster is present
    - local_action:
        module: cs_cluster
        name: kvm-cluster-01
        zone: ch-zrh-ix-01
        hypervisor: KVM
        cluster_type: CloudManaged
    
    # Ensure a cluster is disabled
    - local_action:
        module: cs_cluster
        name: kvm-cluster-01
        zone: ch-zrh-ix-01
        state: disabled
    
    # Ensure a cluster is enabled
    - local_action:
        module: cs_cluster
        name: kvm-cluster-01
        zone: ch-zrh-ix-01
        state: enabled
    
    # Ensure a cluster is absent
    - local_action:
        module: cs_cluster
        name: kvm-cluster-01
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
        <td> cpu_overcommit_ratio </td>
        <td> The CPU overcommit ratio of the cluster. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.0 </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the cluster. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> cluster01 </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the cluster is in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> cluster_type </td>
        <td> Type of the cluster. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ExternalManaged </td>
    </tr>
            <tr>
        <td> ovm3_vip </td>
        <td> Ovm3 VIP to use for pooling and/or clustering </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.10.10.101 </td>
    </tr>
            <tr>
        <td> managed_state </td>
        <td> Whether this cluster is managed by CloudStack. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Managed </td>
    </tr>
            <tr>
        <td> memory_overcommit_ratio </td>
        <td> The memory overcommit ratio of the cluster. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.0 </td>
    </tr>
            <tr>
        <td> hypervisor </td>
        <td> Hypervisor of the cluster </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> VMware </td>
    </tr>
            <tr>
        <td> pod </td>
        <td> Name of pod the cluster is in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> pod01 </td>
    </tr>
            <tr>
        <td> allocation_state </td>
        <td> State of the cluster. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Enabled </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the cluster. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 04589590-ac63-4ffc-93f5-b698b8ac38b6 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
.. note:: This module supports check mode.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

