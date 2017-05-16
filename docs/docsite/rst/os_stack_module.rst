.. _os_stack:


os_stack - Add/Remove Heat Stack
++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or Remove a Stack to an OpenStack Heat


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
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
                <tr><td>endpoint_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>public</td>
        <td><ul><li>public</li><li>internal</li><li>admin</li></ul></td>
        <td><div>Endpoint URL type to fetch from the service catalog.</div>        </td></tr>
                <tr><td>environment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of environment files that should be used for the stack creation</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A path to a client key to use as part of the SSL transaction.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the stack that should be created, name could be char and digit, no space</div>        </td></tr>
                <tr><td>parameters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Dictionary of parameters for the stack creation</div>        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the region.</div>        </td></tr>
                <tr><td>rollback<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rollback stack creation</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Path of the template file to use for the stack creation</div>        </td></tr>
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

    ---
    - name: create stack
      ignore_errors: True
      register: stack_create
      os_stack:
        name: "{{ stack_name }}"
        state: present
        template: "/path/to/my_stack.yaml"
        environment:
        - /path/to/resource-registry.yaml
        - /path/to/environment.yaml
        parameters:
            bmc_flavor: m1.medium
            bmc_image: CentOS
            key_name: default
            private_net: "{{ private_net_param }}"
            node_count: 2
            name: undercloud
            image: CentOS
            my_flavor: m1.large
            external_net: "{{ external_net_param }}"

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
        <td> id </td>
        <td> Stack ID. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 97a3f543-8136-4570-920e-fd7605c989d6 </td>
    </tr>
            <tr>
        <td> stack </td>
        <td> {'sample': 'HOT template to create a new instance and networks', 'type': 'string', 'description': 'Description of the Stack provided in the heat template.'} </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
        
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
