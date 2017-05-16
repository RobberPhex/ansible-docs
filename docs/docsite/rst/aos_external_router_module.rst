.. _aos_external_router:


aos_external_router - Manage AOS External Router
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS External Router module let you manage your External Router easily. You can create create and delete External Router by Name, ID or by using a JSON File. This module is idempotent and support the *check* mode. It's using the AOS REST API.


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
                <tr><td>asn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>ASN id of the external_router.</div>        </td></tr>
                <tr><td>content<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Datastructure of the External Router to create. The format is defined by the <em>content_format</em> parameter. It's the same datastructure that is returned on success in <em>value</em>.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AOS Id of the External Router to manage (can't be used to create a new External Router), Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>loopback<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IP address of the Loopback interface of the external_router.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the External Router to manage. Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate what is the expected state of the External Router (present or not).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: "Create an External Router"
      aos_external_router:
        session: "{{ aos_session }}"
        name: "my-external-router"
        loopback: 10.0.0.1
        asn: 65000
        state: present
    
    - name: "Check if an External Router exist by ID"
      aos_external_router:
        session: "{{ aos_session }}"
        name: "45ab26fc-c2ed-4307-b330-0870488fa13e"
        state: present
    
    - name: "Delete an External Router by name"
      aos_external_router:
        session: "{{ aos_session }}"
        name: "my-external-router"
        state: absent
    
    - name: "Delete an External Router by id"
      aos_external_router:
        session: "{{ aos_session }}"
        id: "45ab26fc-c2ed-4307-b330-0870488fa13e"
        state: absent
    
    # Save an External Router to a file
    - name: "Access External Router 1/3"
      aos_external_router:
        session: "{{ aos_session }}"
        name: "my-external-router"
        state: present
      register: external_router
    
    - name: "Save External Router into a file in JSON 2/3"
      copy:
        content: "{{ external_router.value | to_nice_json }}"
        dest: external_router_saved.json
    
    - name: "Save External Router into a file in YAML 3/3"
      copy:
        content: "{{ external_router.value | to_nice_yaml }}"
        dest: external_router_saved.yaml
    
    - name: "Load External Router from a JSON file"
      aos_external_router:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/external_router_saved.json') }}"
        state: present
    
    - name: "Load External Router from a YAML file"
      aos_external_router:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/external_router_saved.yaml') }}"
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
