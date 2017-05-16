.. _vmware_cluster:


vmware_cluster - Create VMware vSphere Cluster
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create VMware vSphere Cluster


Requirements (on host that executes module)
-------------------------------------------

  * Tested on ESXi 5.5
  * PyVmomi installed


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
                <tr><td>cluster_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the cluster that will be created</div>        </td></tr>
                <tr><td>datacenter_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the datacenter the cluster will be created in.</div>        </td></tr>
                <tr><td>enable_drs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If set to True will enable DRS when the cluster is created.</div>        </td></tr>
                <tr><td>enable_ha<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If set to True will enable HA when the cluster is created.</div>        </td></tr>
                <tr><td>enable_vsan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If set to True will enable vSAN when the cluster is created.</div>        </td></tr>
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

    # Example vmware_cluster command from Ansible Playbooks
    - name: Create Cluster
      local_action:
        module: vmware_cluster
        hostname: "{{ ansible_ssh_host }}"
        username: root
        password: vmware
        datacenter_name: "datacenter"
        cluster_name: "cluster"
        enable_ha: True
        enable_drs: True
        enable_vsan: True





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
