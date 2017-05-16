.. _aos_asn_pool:


aos_asn_pool - Manage AOS ASN Pool
++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS ASN Pool module let you manage your ASN Pool easily. You can create and delete ASN Pool by Name, ID or by using a JSON File. This module is idempotent and support the *check* mode. It's using the AOS REST API.


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
        <td><div>Datastructure of the ASN Pool to manage. The data can be in YAML / JSON or directly a variable. It's the same datastructure that is returned on success in <em>value</em>.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AOS Id of the ASN Pool to manage. Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the ASN Pool to manage. Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>ranges<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of ASNs ranges to add to the ASN Pool. Each range must have 2 values.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate what is the expected state of the ASN Pool (present or not).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: "Create ASN Pool"
      aos_asn_pool:
        session: "{{ aos_session }}"
        name: "my-asn-pool"
        ranges:
          - [ 100, 200 ]
        state: present
      register: asnpool
    
    - name: "Save ASN Pool into a file in JSON"
      copy:
        content: "{{ asnpool.value | to_nice_json }}"
        dest: resources/asn_pool_saved.json
    
    - name: "Save ASN Pool into a file in YAML"
      copy:
        content: "{{ asnpool.value | to_nice_yaml }}"
        dest: resources/asn_pool_saved.yaml
    
    
    - name: "Delete ASN Pool"
      aos_asn_pool:
        session: "{{ aos_session }}"
        name: "my-asn-pool"
        state: absent
    
    - name: "Load ASN Pool from File(JSON)"
      aos_asn_pool:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/asn_pool_saved.json') }}"
        state: present
    
    - name: "Delete ASN Pool from File(JSON)"
      aos_asn_pool:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/asn_pool_saved.json') }}"
        state: absent
    
    - name: "Load ASN Pool from File(Yaml)"
      aos_asn_pool:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/asn_pool_saved.yaml') }}"
        state: present
      register: test
    
    - name: "Delete ASN Pool from File(Yaml)"
      aos_asn_pool:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/asn_pool_saved.yaml') }}"
        state: absent





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
