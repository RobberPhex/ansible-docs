.. _aos_ip_pool:


aos_ip_pool - Manage AOS IP Pool
++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS Ip Pool module let you manage your IP Pool easily. You can create create and delete IP Pool by Name, ID or by using a JSON File. This module is idempotent and support the *check* mode. It's using the AOS REST API.


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
        <td><div>Datastructure of the IP Pool to manage. The data can be in YAML / JSON or directly a variable. It's the same datastructure that is returned on success in <em>value</em>.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AOS Id of the IP Pool to manage (can't be used to create a new IP Pool), Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the IP Pool to manage. Only one of <em>name</em>, <em>id</em> or <em>content</em> can be set.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate what is the expected state of the IP Pool (present or not).</div>        </td></tr>
                <tr><td>subnets<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of subnet that needs to be part of the IP Pool.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: "Create an IP Pool with one subnet"
      aos_ip_pool:
        session: "{{ aos_session }}"
        name: "my-ip-pool"
        subnets: [ 172.10.0.0/16 ]
        state: present
    
    - name: "Create an IP Pool with multiple subnets"
      aos_ip_pool:
        session: "{{ aos_session }}"
        name: "my-other-ip-pool"
        subnets: [ 172.10.0.0/16, 192.168.0.0./24 ]
        state: present
    
    - name: "Check if an IP Pool exist with same subnets by ID"
      aos_ip_pool:
        session: "{{ aos_session }}"
        name: "45ab26fc-c2ed-4307-b330-0870488fa13e"
        subnets: [ 172.10.0.0/16, 192.168.0.0./24 ]
        state: present
    
    - name: "Delete an IP Pool by name"
      aos_ip_pool:
        session: "{{ aos_session }}"
        name: "my-ip-pool"
        state: absent
    
    - name: "Delete an IP pool by id"
      aos_ip_pool:
        session: "{{ aos_session }}"
        id: "45ab26fc-c2ed-4307-b330-0870488fa13e"
        state: absent
    
    # Save an IP Pool to a file
    
    - name: "Access IP Pool 1/3"
      aos_ip_pool:
        session: "{{ aos_session }}"
        name: "my-ip-pool"
        subnets: [ 172.10.0.0/16, 172.12.0.0/16 ]
        state: present
      register: ip_pool
    
    - name: "Save Ip Pool into a file in JSON 2/3"
      copy:
        content: "{{ ip_pool.value | to_nice_json }}"
        dest: ip_pool_saved.json
    
    - name: "Save Ip Pool into a file in YAML 3/3"
      copy:
        content: "{{ ip_pool.value | to_nice_yaml }}"
        dest: ip_pool_saved.yaml
    
    - name: "Load IP Pool from a JSON file"
      aos_ip_pool:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/ip_pool_saved.json') }}"
        state: present
    
    - name: "Load IP Pool from a YAML file"
      aos_ip_pool:
        session: "{{ aos_session }}"
        content: "{{ lookup('file', 'resources/ip_pool_saved.yaml') }}"
        state: present
    
    - name: "Load IP Pool from a Variable"
      aos_ip_pool:
        session: "{{ aos_session }}"
        content:
          display_name: my-ip-pool
          id: 4276738d-6f86-4034-9656-4bff94a34ea7
          subnets:
            - network: 172.10.0.0/16
            - network: 172.12.0.0/16
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
