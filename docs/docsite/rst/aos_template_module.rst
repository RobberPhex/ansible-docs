.. _aos_template:


aos_template - Manage AOS Template
++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS Template module let you manage your Template easily. You can create create and delete Template by Name, ID or by using a JSON File. This module is idempotent and support the *check* mode. It's using the AOS REST API.


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
        <td><div>Datastructure of the Template to create. The data can be in YAML / JSON or directly a variable. It's the same datastructure that is returned on success in <em>value</em>.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AOS Id of the Template to manage (can't be used to create a new Template), Only one of <em>name</em>, <em>id</em> or <em>src</em> can be set.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the Template to manage. Only one of <em>name</em>, <em>id</em> or <em>src</em> can be set.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate what is the expected state of the Template (present or not).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: "Check if an Template exist by name"
      aos_template:
        session: "{{ aos_session }}"
        name: "my-template"
        state: present
    
    - name: "Check if an Template exist by ID"
      aos_template:
        session: "{{ aos_session }}"
        id: "45ab26fc-c2ed-4307-b330-0870488fa13e"
        state: present
    
    - name: "Delete an Template by name"
      aos_template:
        session: "{{ aos_session }}"
        name: "my-template"
        state: absent
    
    - name: "Delete an Template by id"
      aos_template:
        session: "{{ aos_session }}"
        id: "45ab26fc-c2ed-4307-b330-0870488fa13e"
        state: absent
    
    - name: "Access Template 1/3"
      aos_template:
        session: "{{ aos_session }}"
        name: "my-template"
        state: present
      register: template
    - name: "Save Template into a JSON file 2/3"
      copy:
        content: "{{ template.value | to_nice_json }}"
        dest: template_saved.json
    - name: "Save Template into a YAML file 2/3"
      copy:
        content: "{{ template.value | to_nice_yaml }}"
        dest: template_saved.yaml
    
    - name: "Load Template from File (Json)"
      aos_template:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/template_saved.json') }}"
        state: present
    
    - name: "Load Template from File (yaml)"
      aos_template:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/template_saved.yaml') }}"
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
