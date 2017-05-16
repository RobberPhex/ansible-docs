.. _aos_blueprint_param:


aos_blueprint_param - Manage AOS blueprint parameter values
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS Blueprint Parameter module let you manage your Blueprint Parameter easily. You can create access, define and delete Blueprint Parameter. The list of Parameters supported is different per Blueprint. The option *get_param_list* can help you to access the list of supported Parameters for your blueprint. This module is idempotent and support the *check* mode. It's using the AOS REST API.


Requirements (on host that executes module)
-------------------------------------------

  * aos-pyez >= 0.6.0


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
                <tr><td>blueprint<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Blueprint Name or Id as defined in AOS.</div>        </td></tr>
                <tr><td>get_param_list<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get the complete list of supported parameters for this blueprint and the description of those parameters.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of blueprint parameter, as defined by AOS design template. You can use the option <em>get_param_list</em> to get the complete list of supported parameters for your blueprint.</div>        </td></tr>
                <tr><td>param_map<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Defines the aos-pyez collection that will is used to map the user-defined item name into the AOS unique ID value.  For example, if the caller provides an IP address pool <em>param_value</em> called "Server-IpAddrs", then the aos-pyez collection is 'IpPools'. Some <em>param_map</em> are already defined by default like <em>logical_device_maps</em>.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate what is the expected state of the Blueprint Parameter (present or not).</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Blueprint parameter value.  This value may be transformed by using the <em>param_map</em> field; used when the the blueprint parameter requires an AOS unique ID value.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: Add Logical Device Maps information in a Blueprint
      aos_blueprint_param:
        session: "{{ aos_session }}"
        blueprint: "my-blueprint-l2"
        name: "logical_device_maps"
        value:
          spine_1: CumulusVX-Spine-Switch
          spine_2: CumulusVX-Spine-Switch
          leaf_1: CumulusVX-Leaf-Switch
          leaf_2: CumulusVX-Leaf-Switch
          leaf_3: CumulusVX-Leaf-Switch
        state: present
    
    - name: Access Logical Device Maps information from a Blueprint
      aos_blueprint_param:
        session: "{{ aos_session }}"
        blueprint: "my-blueprint-l2"
        name: "logical_device_maps"
        state: present
    
    - name: Reset Logical Device Maps information in a Blueprint
      aos_blueprint_param:
        session: "{{ aos_session }}"
        blueprint: "my-blueprint-l2"
        name: "logical_device_maps"
        state: absent
    
    - name: Get list of all supported Params for a blueprint
      aos_blueprint_param:
        session: "{{ aos_session }}"
        blueprint: "my-blueprint-l2"
        get_param_list: yes
      register: params_list
    - debug: var=params_list
    
    - name: Add Resource Pools information in a Blueprint, by providing a param_map
      aos_blueprint_param:
        session: "{{ aos_session }}"
        blueprint: "my-blueprint-l2"
        name: "resource_pools"
        value:
            leaf_loopback_ips: ['Switches-IpAddrs']
            spine_loopback_ips: ['Switches-IpAddrs']
            spine_leaf_link_ips: ['Switches-IpAddrs']
            spine_asns: ['Private-ASN-pool']
            leaf_asns: ['Private-ASN-pool']
            virtual_network_svi_subnets: ['Servers-IpAddrs']
        param_map:
            leaf_loopback_ips: IpPools
            spine_loopback_ips: IpPools
            spine_leaf_link_ips: IpPools
            spine_asns: AsnPools
            leaf_asns: AsnPools
            virtual_network_svi_subnets: IpPools
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
