.. _vmware_vsan_cluster:


vmware_vsan_cluster - Configure VSAN clustering on an ESXi host
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module can be used to configure VSAN clustering on an ESXi host


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * PyVmomi


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
                <tr><td>cluster_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Desired cluster UUID</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the vSphere vCenter.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: pass, pwd<div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: user, admin<div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Allows connection when SSL certificates are not valid. Set to false when certificates are not trusted.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example command from Ansible Playbook
    
    - name: Configure VMware VSAN Cluster
      hosts: deploy_node
      gather_facts: False
      tags:
        - vsan
      tasks:
        - name: Configure VSAN on first host
          vmware_vsan_cluster:
             hostname: "{{ groups['esxi'][0] }}"
             username: "{{ esxi_username }}"
             password: "{{ site_password }}"
          register: vsan_cluster
    
        - name: Configure VSAN on remaining hosts
          vmware_vsan_cluster:
             hostname: "{{ item }}"
             username: "{{ esxi_username }}"
             password: "{{ site_password }}"
             cluster_uuid: "{{ vsan_cluster.cluster_uuid }}"
          with_items: "{{ groups['esxi'][1:] }}"
    


Notes
-----

.. note::
    - Tested on vSphere 5.5



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
