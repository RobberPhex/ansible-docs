.. _aos_blueprint_virtnet:


aos_blueprint_virtnet - Manage AOS blueprint parameter values
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS Blueprint Virtual Network module let you manage your Virtual Network easily. You can create access, define and delete Virtual Network by name or by using a JSON / Yaml file. This module is idempotent and support the *check* mode. It's using the AOS REST API.


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
                <tr><td>content<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Datastructure of the Virtual Network to manage. The data can be in YAML / JSON or directly a variable. It's the same datastructure that is returned on success in <em>value</em>.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of Virtual Network as part of the Blueprint.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate what is the expected state of the Virtual Network (present or not).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: "Access Existing Virtual Network"
      aos_blueprint_virtnet:
        session: "{{ aos_session }}"
        blueprint: "my-blueprint-l2"
        name: "my-virtual-network"
        state: present
    
    - name: "Delete Virtual Network with JSON File"
      aos_blueprint_virtnet:
        session: "{{ aos_session }}"
        blueprint: "my-blueprint-l2"
        content: "{{ lookup('file', 'resources/virtual-network-02.json') }}"
        state: absent
    
    - name: "Create Virtual Network"
      aos_blueprint_virtnet:
        session: "{{ aos_session }}"
        blueprint: "my-blueprint-l2"
        content: "{{ lookup('file', 'resources/virtual-network-02.json') }}"
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
