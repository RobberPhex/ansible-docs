.. _virt_pool:


virt_pool - Manage libvirt storage pools
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage *libvirt* storage pools.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python-libvirt
  * python-lxml


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
    <td>autostart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specify if a given storage pool should be started automatically on system boot.</div></td></tr>
            <tr>
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>define</li><li>build</li><li>create</li><li>start</li><li>stop</li><li>destroy</li><li>delete</li><li>undefine</li><li>get_xml</li><li>list_pools</li><li>facts</li><li>info</li><li>status</li></ul></td>
        <td><div>in addition to state management, various non-idempotent commands are available. See examples.</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>new</li><li>repair</li><li>resize</li><li>no_overwrite</li><li>overwrite</li><li>normal</li><li>zeroed</li></ul></td>
        <td><div>Pass additional parameters to 'build' or 'delete' commands.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the storage pool being managed. Note that pool must be previously defined with xml.</div></br>
        <div style="font-size: small;">aliases: pool<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>active</li><li>inactive</li><li>present</li><li>absent</li><li>undefined</li><li>deleted</li></ul></td>
        <td><div>specify which state you want a storage pool to be in. If 'active', pool will be started. If 'present', ensure that pool is present but do not change its state; if it's missing, you need to specify xml argument. If 'inactive', pool will be stopped. If 'undefined' or 'absent', pool will be removed from <em>libvirt</em> configuration. If 'deleted', pool contents will be deleted and then pool undefined.</div></td></tr>
            <tr>
    <td>uri<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>qemu:///system</td>
        <td><ul></ul></td>
        <td><div><em>libvirt</em> connection uri.</div></td></tr>
            <tr>
    <td>xml<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>XML document used with the define command.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Define a new storage pool
    - virt_pool: command=define name=vms xml='{{ lookup("template", "pool/dir.xml.j2") }}'
    
    # Build a storage pool if it does not exist
    - virt_pool: command=build name=vms
    
    # Start a storage pool
    - virt_pool: command=create name=vms
    
    # List available pools
    - virt_pool: command=list_pools
    
    # Get XML data of a specified pool
    - virt_pool: command=get_xml name=vms
    
    # Stop a storage pool
    - virt_pool: command=destroy name=vms
    
    # Delete a storage pool (destroys contents)
    - virt_pool: command=delete name=vms
    
    # Undefine a storage pool
    - virt_pool: command=undefine name=vms
    
    # Gather facts about storage pools
    # Facts will be available as 'ansible_libvirt_pools'
    - virt_pool: command=facts
    
    # Gather information about pools managed by 'libvirt' remotely using uri
    - virt_pool: command=info uri='{{ item }}'
      with_items: libvirt_uris
      register: storage_pools
    
    # Ensure that a pool is active (needs to be defined and built first)
    - virt_pool: state=active name=vms
    
    # Ensure that a pool is inactive
    - virt_pool: state=inactive name=vms
    
    # Ensure that a given pool will be started at boot
    - virt_pool: autostart=yes name=vms
    
    # Disable autostart for a given pool
    - virt_pool: autostart=no name=vms




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

