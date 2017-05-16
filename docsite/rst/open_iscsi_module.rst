.. _open_iscsi:


open_iscsi - Manage iscsi targets with open-iscsi
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Discover targets on given portal, (dis)connect targets, mark targets to manually or auto start, return device nodes of connected targets.


Requirements
------------

  * open_iscsi library and tools (iscsiadm)


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
    <td>auto_node_startup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>whether the target node should be automatically connected at startup</div></br>
        <div style="font-size: small;">aliases: automatic<div></td></tr>
            <tr>
    <td>discover<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>whether the list of target nodes on the portal should be (re)discovered and added to the persistent iscsi database. Keep in mind that iscsiadm discovery resets configurtion, like node.startup to manual, hence combined with auto_node_startup=yes will allways return a changed state.</div></td></tr>
            <tr>
    <td>login<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>whether the target node should be connected</div></td></tr>
            <tr>
    <td>node_auth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>CHAP</td>
        <td><ul></ul></td>
        <td><div>discovery.sendtargets.auth.authmethod</div></td></tr>
            <tr>
    <td>node_pass<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>discovery.sendtargets.auth.password</div></td></tr>
            <tr>
    <td>node_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>discovery.sendtargets.auth.username</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3260</td>
        <td><ul></ul></td>
        <td><div>the port on which the iscsi target process listens</div></td></tr>
            <tr>
    <td>portal<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the ip address of the iscsi target</div></br>
        <div style="font-size: small;">aliases: ip<div></td></tr>
            <tr>
    <td>show_nodes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>whether the list of nodes in the persistent iscsi database should be returned by the module</div></td></tr>
            <tr>
    <td>target<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the iscsi target name</div></br>
        <div style="font-size: small;">aliases: name, targetname<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # perform a discovery on 10.1.2.3 and show available target nodes
    - open_iscsi: show_nodes=yes discover=yes portal=10.1.2.3
    
    # discover targets on portal and login to the one available
    # (only works if exactly one target is exported to the initiator)
    - open_iscsi: portal={{iscsi_target}} login=yes discover=yes
    
    # description: connect to the named target, after updating the local
    # persistent database (cache)
    - open_iscsi: login=yes target=iqn.1986-03.com.sun:02:f8c1f9e0-c3ec-ec84-c9c9-8bfb0cd5de3d
    
    # description: discconnect from the cached named target
    - open_iscsi: login=no target=iqn.1986-03.com.sun:02:f8c1f9e0-c3ec-ec84-c9c9-8bfb0cd5de3d"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

