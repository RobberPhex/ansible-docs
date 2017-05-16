.. _aos_rack_type:


aos_rack_type - Manage AOS Rack Type
++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS Rack Type module let you manage your Rack Type easily. You can create create and delete Rack Type by Name, ID or by using a JSON File. This module is idempotent and support the *check* mode. It's using the AOS REST API.


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
        <td><div>Datastructure of the Rack Type to create. The data can be in YAML / JSON or directly a variable. It's the same datastructure that is returned on success in <em>value</em>.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AOS Id of the Rack Type to manage (can't be used to create a new Rack Type), Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the Rack Type to manage. Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate what is the expected state of the Rack Type (present or not).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: "Delete a Rack Type by name"
      aos_rack_type:
        session: "{{ aos_session }}"
        name: "my-rack-type"
        state: absent
    
    - name: "Delete a Rack Type by id"
      aos_rack_type:
        session: "{{ aos_session }}"
        id: "45ab26fc-c2ed-4307-b330-0870488fa13e"
        state: absent
    
    # Save a Rack Type to a file
    
    - name: "Access Rack Type 1/3"
      aos_rack_type:
        session: "{{ aos_session }}"
        name: "my-rack-type"
        state: present
      register: rack_type
    - name: "Save Rack Type into a JSON file 2/3"
      copy:
        content: "{{ rack_type.value | to_nice_json }}"
        dest: rack_type_saved.json
    - name: "Save Rack Type into a YAML file 3/3"
      copy:
        content: "{{ rack_type.value | to_nice_yaml }}"
        dest: rack_type_saved.yaml
    
    - name: "Load Rack Type from a JSON file"
      aos_rack_type:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/rack_type_saved.json') }}"
        state: present
    
    - name: "Load Rack Type from a YAML file"
      aos_rack_type:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/rack_type_saved.yaml') }}"
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
