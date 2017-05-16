.. _open_iscsi:


open_iscsi - Manage iscsi targets with open-iscsi
+++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Discover targets on given portal, (dis)connect targets, mark targets to manually or auto start, return device nodes of connected targets.

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
    <td>auto_node_startup</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>whether the target node should be automatically connected at startup</td>
    </tr>
            <tr>
    <td>discover</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>whether the list of target nodes on the portal should be (re)discovered and added to the persistent iscsi database. Keep in mind that iscsiadm discovery resets configurtion, like node.startup to manual, hence combined with auto_node_startup=yes will allways return a changed state.</td>
    </tr>
            <tr>
    <td>login</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>whether the target node should be connected</td>
    </tr>
            <tr>
    <td>node_auth</td>
    <td>no</td>
    <td>CHAP</td>
        <td><ul></ul></td>
        <td>discovery.sendtargets.auth.authmethod</td>
    </tr>
            <tr>
    <td>node_pass</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>discovery.sendtargets.auth.password</td>
    </tr>
            <tr>
    <td>node_user</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>discovery.sendtargets.auth.username</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>3260</td>
        <td><ul></ul></td>
        <td>the port on which the iscsi target process listens</td>
    </tr>
            <tr>
    <td>portal</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the ip address of the iscsi target</td>
    </tr>
            <tr>
    <td>show_nodes</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>whether the list of nodes in the persistent iscsi database should be returned by the module</td>
    </tr>
            <tr>
    <td>target</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the iscsi target name</td>
    </tr>
        </table>


.. note:: Requires open_iscsi library and tools (iscsiadm)


Examples
--------

.. raw:: html

    <p>perform a discovery on 10.1.2.3 and show available target nodes</p>    <p>
    <pre>
    open_iscsi: show_nodes=yes discover=yes portal=10.1.2.3
    </pre>
    </p>
    <p>discover targets on portal and login to the one available (only works if exactly one target is exported to the initiator)</p>    <p>
    <pre>
    open_iscsi: portal={{iscsi_target}} login=yes discover=yes
    </pre>
    </p>
    <p>connect to the named target, after updating the local persistent database (cache)</p>    <p>
    <pre>
    open_iscsi: login=yes target=iqn.1986-03.com.sun:02:f8c1f9e0-c3ec-ec84-c9c9-8bfb0cd5de3d
    </pre>
    </p>
    <p>discconnect from the cached named target</p>    <p>
    <pre>
    open_iscsi: login=no target=iqn.1986-03.com.sun:02:f8c1f9e0-c3ec-ec84-c9c9-8bfb0cd5de3d&#34;
    </pre>
    </p>
    <br/>




    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

