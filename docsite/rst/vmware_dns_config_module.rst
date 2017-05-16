.. _vmware_dns_config:


vmware_dns_config - Manage VMware ESXi DNS Configuration
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage VMware ESXi DNS Configuration


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
            <tr>
    <td>change_hostname_to<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hostname that an ESXi host should be changed to.</div></td></tr>
            <tr>
    <td>dns_servers<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The DNS servers that the host should be configured to use.</div></td></tr>
            <tr>
    <td>domainname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The domain the ESXi host should be apart of.</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hostname or IP address of the vSphere vCenter</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password of the vSphere vCenter</div></br>
        <div style="font-size: small;">aliases: pass, pwd<div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username of the vSphere vCenter</div></br>
        <div style="font-size: small;">aliases: user, admin<div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Allows connection when SSL certificates are not valid. Set to false when certificates are not trusted</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example vmware_dns_config command from Ansible Playbooks
    - name: Configure ESXi hostname and DNS servers
      local_action:
        module: vmware_dns_config
        hostname: esxi_hostname
        username: root
        password: your_password
        change_hostname_to: esx01
        domainname: foo.org
        dns_servers:
            - 8.8.8.8
            - 8.8.4.4


Notes
-----

.. note:: Tested on vSphere 5.5


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

