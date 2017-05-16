.. _aos_blueprint:


aos_blueprint - Manage AOS blueprint instance
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS Blueprint module let you manage your Blueprint easily. You can create create and delete Blueprint by Name or ID. You can also use it to retrieve all data from a blueprint. This module is idempotent and support the *check* mode. It's using the AOS REST API.


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
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AOS Id of the IP Pool to manage (can't be used to create a new IP Pool). Only one of <em>name</em> or <em>id</em> can be set.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the Blueprint to manage. Only one of <em>name</em> or <em>id</em> can be set.</div>        </td></tr>
                <tr><td>reference_arch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When creating a blueprint, this value identifies a known AOS reference architecture value. <em>Refer to AOS-server documentation for available values</em>.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>build-ready</li></ul></td>
        <td><div>Indicate what is the expected state of the Blueprint.</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When creating a blueprint, this value identifies, by name, an existing engineering design template within the AOS-server.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td></td>
        <td><div>When <em>state=build-ready</em>, this timeout identifies timeout in seconds to wait before declaring a failure.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Creating blueprint
      aos_blueprint:
        session: "{{ aos_session }}"
        name: "my-blueprint"
        template: "my-template"
        reference_arch: two_stage_l3clos
        state: present
    
    - name: Access a blueprint and get content
      aos_blueprint:
        session: "{{ aos_session }}"
        name: "{{ blueprint_name }}"
        template: "{{ blueprint_template }}"
        state: present
      register: bp
    
    - name: Delete a blueprint
      aos_blueprint:
        session: "{{ aos_session }}"
        name: "my-blueprint"
        state: absent
    
    - name: Await blueprint build-ready, and obtain contents
      aos_blueprint:
        session: "{{ aos_session }}"
        name: "{{ blueprint_name }}"
        state: build-ready
      register: bp





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
