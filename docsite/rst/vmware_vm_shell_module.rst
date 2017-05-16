.. _vmware_vm_shell:


vmware_vm_shell - Execute a process in VM
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Start a program in a VM without the need for network connection


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
    <td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The cluster hosting the VM</div><div>Will help speed up search</div></td></tr>
            <tr>
    <td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The datacenter hosting the VM</div><div>Will help speed up search</div></td></tr>
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
            <tr>
    <td>vm_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The identification for the VM</div></td></tr>
            <tr>
    <td>vm_id_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>vm_name</td>
        <td><ul><li>uuid</li><li>dns_name</li><li>inventory_path</li><li>vm_name</li></ul></td>
        <td><div>The identification tag for the VM</div></td></tr>
            <tr>
    <td>vm_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The password used to login to the VM.</div></td></tr>
            <tr>
    <td>vm_shell<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The absolute path to the program to start. On Linux this is executed via bash.</div></td></tr>
            <tr>
    <td>vm_shell_args<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The argument to the program.</div></td></tr>
            <tr>
    <td>vm_shell_cwd<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The current working directory of the application from which it will be run</div></td></tr>
            <tr>
    <td>vm_shell_env<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Comma seperated list of envirnoment variable, specified in the guest OS notation</div></td></tr>
            <tr>
    <td>vm_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The user to connect to the VM.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

        - name: shell execution
          local_action:
            module: vmware_vm_shell
            hostname: myVSphere
            username: myUsername
            password: mySecret
            datacenter: myDatacenter
            vm_id: NameOfVM
            vm_username: root
            vm_password: superSecret
            vm_shell: /bin/echo
            vm_shell_args: " $var >> myFile "
            vm_shell_env:
              - "PATH=/bin"
              - "VAR=test"
            vm_shell_cwd: "/tmp"
    


Notes
-----

.. note:: Tested on vSphere 5.5
.. note:: Only the first match against vm_id is used, even if there are multiple matches


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

