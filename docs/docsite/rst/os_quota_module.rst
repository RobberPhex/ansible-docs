.. _os_quota:


os_quota - Manage OpenStack Quotas
++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage OpenStack Quotas. Quotas can be created, updated or deleted using this module. A quota will be updated if matches an existing project and is present.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python >= 2.7
  * shade
  * shade > 1.9.0


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
                <tr><td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>How long should the socket layer wait before timing out for API calls. If this is omitted, nothing will be passed to the requests library.</div>        </td></tr>
                <tr><td>auth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary containing auth information as needed by the cloud's auth plugin strategy. For the default <em>password</em> plugin, this would contain <em>auth_url</em>, <em>username</em>, <em>password</em>, <em>project_name</em> and any information about domains if the cloud supports them. For other plugins, this param will need to contain whatever parameters that auth plugin requires. This parameter is not needed if a named cloud is provided or OpenStack OS_* environment variables are present.</div>        </td></tr>
                <tr><td>auth_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>password</td>
        <td></td>
        <td><div>Name of the auth plugin to use. If the cloud uses something other than password authentication, the name of the plugin should be indicated here and the contents of the <em>auth</em> parameter should be updated accordingly.</div>        </td></tr>
                <tr><td>availability_zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ignored. Present for backwards compatability</div>        </td></tr>
                <tr><td>backup_gigabytes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum size of backups in GB's.</div>        </td></tr>
                <tr><td>backups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum number of backups allowed.</div>        </td></tr>
                <tr><td>cacert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a CA Cert bundle that can be used as part of verifying SSL API requests.</div>        </td></tr>
                <tr><td>cert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a client certificate to use as part of the SSL transaction.</div>        </td></tr>
                <tr><td>cloud<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Named cloud to operate against. Provides default values for <em>auth</em> and <em>auth_type</em>. This parameter is not needed if <em>auth</em> is provided or if OpenStack OS_* environment variables are present.</div>        </td></tr>
                <tr><td>cores<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum number of CPU's per project.</div>        </td></tr>
                <tr><td>endpoint_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>public</td>
        <td><ul><li>public</li><li>internal</li><li>admin</li></ul></td>
        <td><div>Endpoint URL type to fetch from the service catalog.</div>        </td></tr>
                <tr><td>fixed_ips<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of fixed IP's to allow.</div>        </td></tr>
                <tr><td>floating_ips<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of floating IP's to allow in Compute.</div></br>
    <div style="font-size: small;">aliases: compute_floating_ips<div>        </td></tr>
                <tr><td>floatingip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of floating IP's to allow in Network.</div></br>
    <div style="font-size: small;">aliases: network_floating_ips<div>        </td></tr>
                <tr><td>gigabytes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum volume storage allowed for project.</div>        </td></tr>
                <tr><td>gigabytes_lvm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum size in GB's of individual lvm volumes.</div>        </td></tr>
                <tr><td>injected_file_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum file size in bytes.</div>        </td></tr>
                <tr><td>injected_files<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of injected files to allow.</div>        </td></tr>
                <tr><td>injected_path_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum path size.</div>        </td></tr>
                <tr><td>instances<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum number of instances allowed.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a client key to use as part of the SSL transaction.</div>        </td></tr>
                <tr><td>key_pairs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of key pairs to allow.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the OpenStack Project to manage.</div>        </td></tr>
                <tr><td>network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of networks to allow.</div>        </td></tr>
                <tr><td>per_volume_gigabytes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum size in GB's of individual volumes.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of Network ports to allow, this needs to be greater than the instances limit.</div>        </td></tr>
                <tr><td>properties<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of properties to allow.</div>        </td></tr>
                <tr><td>ram<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Maximum amount of ram in MB to allow.</div>        </td></tr>
                <tr><td>rbac_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of policies to allow.</div>        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the region.</div>        </td></tr>
                <tr><td>router<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of routers to allow.</div>        </td></tr>
                <tr><td>security_group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of security groups to allow.</div>        </td></tr>
                <tr><td>security_group_rule<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of rules per security group to allow.</div>        </td></tr>
                <tr><td>server_group_members<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of server group members to allow.</div>        </td></tr>
                <tr><td>server_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of server groups to allow.</div>        </td></tr>
                <tr><td>snapshots<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of snapshots to allow.</div>        </td></tr>
                <tr><td>snapshots_lvm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of LVM snapshots to allow.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td></td>
        <td><div>A value of present sets the quota and a value of absent resets the quota to system defaults.</div>        </td></tr>
                <tr><td>subnet<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of subnets to allow.</div>        </td></tr>
                <tr><td>subnetpool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of subnet pools to allow.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td></td>
        <td><div>How long should ansible wait for the requested resource.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not SSL API requests should be verified. Before 2.3 this defaulted to True.</div></br>
    <div style="font-size: small;">aliases: verify<div>        </td></tr>
                <tr><td>volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of volumes to allow.</div>        </td></tr>
                <tr><td>volumes_lvm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Number of LVM volumes to allow.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Should ansible wait until the requested resource is complete.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # List a Project Quota
    - os_quota:
        cloud: mycloud
        name: demoproject
    
    # Set a Project back to the defaults
    - os_quota:
        cloud: mycloud
        name: demoproject
        state: absent
    
    # Update a Project Quota for cores
    - os_quota:
        cloud: mycloud
        name: demoproject
        cores: 100
    
    # Update a Project Quota
    - os_quota:
        name: demoproject
        cores: 1000
        volumes: 20
        volumes_type:
          - volume_lvm: 10
    
    # Complete example based on list of projects
    - name: Update quotas
      os_quota:
        name: "{{ item.name }}"
        backup_gigabytes: "{{ item.backup_gigabytes }}"
        backups: "{{ item.backups }}"
        cores: "{{ item.cores }}"
        fixed_ips: "{{ item.fixed_ips }}"
        floating_ips: "{{ item.floating_ips }}"
        floatingip: "{{ item.floatingip }}"
        gigabytes: "{{ item.gigabytes }}"
        injected_file_size: "{{ item.injected_file_size }}"
        injected_files: "{{ item.injected_files }}"
        injected_path_size: "{{ item.injected_path_size }}"
        instances: "{{ item.instances }}"
        port: "{{ item.port }}"
        key_pairs: "{{ item.key_pairs }}"
        per_volume_gigabytes: "{{ item.per_volume_gigabytes }}"
        properties: "{{ item.properties }}"
        ram: "{{ item.ram }}"
        security_group_rule: "{{ item.security_group_rule }}"
        security_group: "{{ item.security_group }}"
        server_group_members: "{{ item.server_group_members }}"
        server_groups: "{{ item.server_groups }}"
        snapshots: "{{ item.snapshots }}"
        volumes: "{{ item.volumes }}"
        volumes_types:
          volumes_lvm: "{{ item.volumes_lvm }}"
        snapshots_types:
          snapshots_lvm: "{{ item.snapshots_lvm }}"
        gigabytes_types:
          gigabytes_lvm: "{{ item.gigabytes_lvm }}"
      with_items:
        - "{{ projects }}"
      when: item.state == "present"

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
        <td> openstack_quotas </td>
        <td> Dictionary describing the project quota. </td>
        <td align=center> Regardless if changes where made or note </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note::
    - The standard OpenStack environment variables, such as ``OS_USERNAME`` may be used instead of providing explicit values.
    - Auth information is driven by os-client-config, which means that values can come from a yaml config file in /etc/ansible/openstack.yaml, /etc/openstack/clouds.yaml or ~/.config/openstack/clouds.yaml, then from standard environment variables, then finally by explicit parameters in plays. More information can be found at http://docs.openstack.org/developer/os-client-config



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
