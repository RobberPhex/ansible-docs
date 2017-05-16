.. _aos_logical_device_map:


aos_logical_device_map - Manage AOS Logical Device Map
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS Logical Device Map module let you manage your Logical Device Map easily. You can create create and delete Logical Device Map by Name, ID or by using a JSON File. This module is idempotent and support the *check* mode. It's using the AOS REST API.


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
                <tr><td>content<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Datastructure of the Logical Device Map to manage. The data can be in YAML / JSON or directly a variable. It's the same datastructure that is returned on success in <em>value</em>. Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AOS Id of the Logical Device Map to manage (can't be used to create a new Logical Device Map), Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the Logical Device Map to manage. Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate what is the expected state of the Logical Device Map (present or not).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: "Create an Logical Device Map with one subnet"
      aos_logical_device_map:
        session: "{{ aos_session }}"
        name: "my-logical-device-map"
        state: present
    
    - name: "Create an Logical Device Map with multiple subnets"
      aos_logical_device_map:
        session: "{{ aos_session }}"
        name: "my-other-logical-device-map"
        state: present
    
    - name: "Check if an Logical Device Map exist with same subnets by ID"
      aos_logical_device_map:
        session: "{{ aos_session }}"
        name: "45ab26fc-c2ed-4307-b330-0870488fa13e"
        state: present
    
    - name: "Delete an Logical Device Map by name"
      aos_logical_device_map:
        session: "{{ aos_session }}"
        name: "my-logical-device-map"
        state: absent
    
    - name: "Delete an Logical Device Map by id"
      aos_logical_device_map:
        session: "{{ aos_session }}"
        id: "45ab26fc-c2ed-4307-b330-0870488fa13e"
        state: absent
    
    # Save an Logical Device Map to a file
    
    - name: "Access Logical Device Map 1/3"
      aos_logical_device_map:
        session: "{{ aos_session }}"
        name: "my-logical-device-map"
        state: present
      register: logical_device_map
    
    - name: "Save Logical Device Map into a file in JSON 2/3"
      copy:
        content: "{{ logical_device_map.value | to_nice_json }}"
        dest: logical_device_map_saved.json
    
    - name: "Save Logical Device Map into a file in YAML 3/3"
      copy:
        content: "{{ logical_device_map.value | to_nice_yaml }}"
        dest: logical_device_map_saved.yaml
    
    - name: "Load Logical Device Map from a JSON file"
      aos_logical_device_map:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/logical_device_map_saved.json') }}"
        state: present
    
    - name: "Load Logical Device Map from a YAML file"
      aos_logical_device_map:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/logical_device_map_saved.yaml') }}"
        state: present
    





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
