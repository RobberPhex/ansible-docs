.. _os_nova_flavor:


os_nova_flavor - Manage OpenStack compute flavors
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove flavors from OpenStack.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * shade


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
                <tr><td>disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Size of local disk, in GB.</div>        </td></tr>
                <tr><td>endpoint_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>public</td>
        <td><ul><li>public</li><li>internal</li><li>admin</li></ul></td>
        <td><div>Endpoint URL type to fetch from the service catalog.</div>        </td></tr>
                <tr><td>ephemeral<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ephemeral space size, in GB.</div>        </td></tr>
                <tr><td>extra_specs<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Metadata dictionary</div>        </td></tr>
                <tr><td>flavorid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>auto</td>
        <td></td>
        <td><div>ID for the flavor. This is optional as a unique UUID will be assigned if a value is not specified.</div>        </td></tr>
                <tr><td>is_public<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Make flavor accessible to the public.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a client key to use as part of the SSL transaction.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Flavor name.</div>        </td></tr>
                <tr><td>ram<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Amount of memory, in MB.</div>        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the region.</div>        </td></tr>
                <tr><td>rxtx_factor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1.0</td>
        <td></td>
        <td><div>RX/TX factor.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource. When <em>state</em> is 'present', then <em>ram</em>, <em>vcpus</em>, and <em>disk</em> are all required. There are no default values for those parameters.</div>        </td></tr>
                <tr><td>swap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Swap space size, in MB.</div>        </td></tr>
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
                <tr><td>vcpus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of virtual CPUs.</div>        </td></tr>
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

    - name: "Create 'tiny' flavor with 1024MB of RAM, 1 virtual CPU, and 10GB of local disk, and 10GB of ephemeral."
      os_nova_flavor:
        cloud: mycloud
        state: present
        name: tiny
        ram: 1024
        vcpus: 1
        disk: 10
        ephemeral: 10
    
    - name: "Delete 'tiny' flavor"
      os_nova_flavor:
        cloud: mycloud
        state: absent
        name: tiny
    
    - name: Create flavor with metadata
      os_nova_flavor:
        cloud: mycloud
        state: present
        name: tiny
        ram: 1024
        vcpus: 1
        disk: 10
        extra_specs:
          "quota:disk_read_iops_sec": 5000
          "aggregate_instance_extra_specs:pinned": false

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
        <td> flavor </td>
        <td> Dictionary describing the flavor. </td>
        <td align=center> On success when I(state) is 'present' </td>
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

                <tr>
        <td> name </td>
        <td> Flavor name. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> tiny </td>
        </tr>
                <tr>
        <td> ram </td>
        <td> Amount of memory, in MB. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 1024 </td>
        </tr>
                <tr>
        <td> ephemeral </td>
        <td> Ephemeral space size, in GB. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
        </tr>
                <tr>
        <td> vcpus </td>
        <td> Number of virtual CPUs. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 2 </td>
        </tr>
                <tr>
        <td> extra_specs </td>
        <td> Flavor metadata </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'aggregate_instance_extra_specs:pinned': False, 'quota:disk_read_iops_sec': 5000} </td>
        </tr>
                <tr>
        <td> swap </td>
        <td> Swap space size, in MB. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 100 </td>
        </tr>
                <tr>
        <td> is_public </td>
        <td> Make flavor accessible to the public. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> disk </td>
        <td> Size of local disk, in GB. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
        </tr>
                <tr>
        <td> id </td>
        <td> Flavor ID. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 515256b8-7027-4d73-aa54-4e30a4a4a339 </td>
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
