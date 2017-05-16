.. _os_ironic:


os_ironic - Create/Delete Bare Metal Resources from OpenStack
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or Remove Ironic nodes from OpenStack.


Requirements (on host that executes module)
-------------------------------------------

  * jsonpatch
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
                <tr><td>chassis_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Associate the node with a pre-defined chassis.</div>        </td></tr>
                <tr><td>cloud<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Named cloud to operate against. Provides default values for <em>auth</em> and <em>auth_type</em>. This parameter is not needed if <em>auth</em> is provided or if OpenStack OS_* environment variables are present.</div>        </td></tr>
                <tr><td>driver<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>The name of the Ironic Driver to use with this node.</div>        </td></tr>
                <tr><td rowspan="2">driver_info<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td><td></td>
    <td> <div>Information for this server's driver. Will vary based on which driver is in use. Any sub-field which is populated will be validated during creation.</div>    </tr>
    <tr>
    <td colspan="5">
    <table border=1 cellpadding=4>
    <caption><b>Dictionary object driver_info</b></caption>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                    <tr><td>management<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>Information necessary to interact with this server's management interface. May be shared by power_info in some cases.</div>        </td></tr>
                    <tr><td>console<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Information necessary to connect to this server's serial console.  Not all drivers support this.</div>        </td></tr>
                    <tr><td>power<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>Information necessary to turn this server on / off. This often includes such things as IPMI username, password, and IP address.</div>        </td></tr>
                    <tr><td>deploy<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Information necessary to deploy this server directly, without using Nova. THIS IS NOT RECOMMENDED.</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>endpoint_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>public</td>
        <td><ul><li>public</li><li>internal</li><li>admin</li></ul></td>
        <td><div>Endpoint URL type to fetch from the service catalog.</div>        </td></tr>
                <tr><td>ironic_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>If noauth mode is utilized, this is required to be set to the endpoint URL for the Ironic API.  Use with "auth" and "auth_type" settings set to None.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a client key to use as part of the SSL transaction.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>unique name identifier to be given to the resource.</div>        </td></tr>
                <tr><td>nics<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A list of network interface cards, eg, " - mac: aa:bb:cc:aa:bb:cc"</div>        </td></tr>
                <tr><td rowspan="2">properties<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td><td></td>
    <td> <div>Definition of the physical characteristics of this server, used for scheduling purposes</div>    </tr>
    <tr>
    <td colspan="5">
    <table border=1 cellpadding=4>
    <caption><b>Dictionary object properties</b></caption>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                    <tr><td>cpu_arch<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>x86_64</td>
                <td></td>
                <td><div>CPU architecture (x86_64, i686, ...)</div>        </td></tr>
                    <tr><td>ram<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>1</td>
                <td></td>
                <td><div>amount of RAM this machine has, in MB</div>        </td></tr>
                    <tr><td>disk_size<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>1</td>
                <td></td>
                <td><div>size of first storage device in this machine (typically /dev/sda), in GB</div>        </td></tr>
                    <tr><td>cpus<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>1</td>
                <td></td>
                <td><div>Number of CPU cores this machine has</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the region.</div>        </td></tr>
                <tr><td>skip_update_of_driver_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Allows the code that would assert changes to nodes to skip the update if the change is a single line consisting of the password field.  As of Kilo, by default, passwords are always masked to API requests, which means the logic as a result always attempts to re-assert the password field.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicates desired state of the resource</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td></td>
        <td><div>How long should ansible wait for the requested resource.</div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>globally unique identifier (UUID) to be given to the resource. Will be auto-generated if not specified, and name is specified.</div><div>Definition of a UUID will always take precedence to a name value.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not SSL API requests should be verified. Before 2.3 this defaulted to True.</div></br>
    <div style="font-size: small;">aliases: verify<div>        </td></tr>
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

    # Enroll a node with some basic properties and driver info
    - os_ironic:
        cloud: "devstack"
        driver: "pxe_ipmitool"
        uuid: "00000000-0000-0000-0000-000000000002"
        properties:
          cpus: 2
          cpu_arch: "x86_64"
          ram: 8192
          disk_size: 64
        nics:
          - mac: "aa:bb:cc:aa:bb:cc"
          - mac: "dd:ee:ff:dd:ee:ff"
        driver_info:
          power:
            ipmi_address: "1.2.3.4"
            ipmi_username: "admin"
            ipmi_password: "adminpass"
        chassis_uuid: "00000000-0000-0000-0000-000000000001"
    


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
