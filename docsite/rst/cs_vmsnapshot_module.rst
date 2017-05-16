.. _cs_vmsnapshot:


cs_vmsnapshot - Manages VM snapshots on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, remove and revert VM from snapshots.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * cs >= 0.6.10


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
    <td>account<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Account the VM snapshot is related to.</div></td></tr>
            <tr>
    <td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div></td></tr>
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td><ul></ul></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div></td></tr>
            <tr>
    <td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Secret key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>HTTP timeout.</div></td></tr>
            <tr>
    <td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Description of the snapshot.</div></td></tr>
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Domain the VM snapshot is related to.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Unique Name of the snapshot. In CloudStack terms display name.</div></br>
        <div style="font-size: small;">aliases: display_name<div></td></tr>
            <tr>
    <td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Poll async jobs until job has finished.</div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the project the VM is assigned to.</div></td></tr>
            <tr>
    <td>snapshot_memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Snapshot memory if set to true.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>revert</li></ul></td>
        <td><div>State of the snapshot.</div></td></tr>
            <tr>
    <td>vm<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the virtual machine.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the zone in which the VM is in. If not set, default zone is used.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a VM snapshot of disk and memory before an upgrade
    - local_action:
        module: cs_vmsnapshot
        name: Snapshot before upgrade
        vm: web-01
        snapshot_memory: yes
    
    # Revert a VM to a snapshot after a failed upgrade
    - local_action:
        module: cs_vmsnapshot
        name: Snapshot before upgrade
        vm: web-01
        state: revert
    
    # Remove a VM snapshot after successful upgrade
    - local_action:
        module: cs_vmsnapshot
        name: Snapshot before upgrade
        vm: web-01
        state: absent

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> current </td>
        <td> true if snapshot is current </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> domain </td>
        <td> Domain the the vm snapshot is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> display_name </td>
        <td> Display name of the snapshot. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> snapshot before update </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the snapshot. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> snapshot before update </td>
    </tr>
            <tr>
        <td> created </td>
        <td> date of the snapshot. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2015-03-29T14:57:06+0200 </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the vm snapshot is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> project </td>
        <td> Name of project the vm snapshot is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state of the vm snapshot </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Allocated </td>
    </tr>
            <tr>
        <td> type </td>
        <td> type of vm snapshot </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> DiskAndMemory </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the snapshot. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> a6f7a5fc-43f8-11e5-a151-feff819cdc9f </td>
    </tr>
            <tr>
        <td> description </td>
        <td> description of vm snapshot </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> snapshot brought to you by Ansible </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
.. note:: A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
.. note:: This module supports check mode.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

