.. _beadm:


beadm - Manage ZFS boot environments on FreeBSD/Solaris/illumos systems.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, delete or activate ZFS boot environments.
* Mount and unmount ZFS boot environments.




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
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Associate a description with a new boot environment. This option is available only on Solarish platforms.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Specifies if the unmount should be forced.</div>        </td></tr>
                <tr><td>mountpoint<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path where to mount the ZFS boot environment</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>ZFS boot environment name.</div></br>
    <div style="font-size: small;">aliases: be<div>        </td></tr>
                <tr><td>options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Create the datasets for new BE with specific ZFS properties. Multiple options can be specified. This option is available only on Solarish platforms.</div>        </td></tr>
                <tr><td>snapshot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If specified, the new boot environment will be cloned from the given snapshot or inactive boot environment.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>activated</li><li>mounted</li><li>unmounted</li></ul></td>
        <td><div>Create or delete ZFS boot environment.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create ZFS boot environment
      beadm:
        name: upgrade-be
        state: present
    
    - name: Create ZFS boot environment from existing inactive boot environment
      beadm:
        name: upgrade-be
        snapshot: be@old
        state: present
    
    - name: Create ZFS boot environment with compression enabled and description "upgrade"
      beadm:
        name: upgrade-be
        options: "compression=on"
        description: upgrade
        state: present
    
    - name: Delete ZFS boot environment
      beadm:
        name: old-be
        state: absent
    
    - name: Mount ZFS boot environment on /tmp/be
      beadm:
        name: BE
        mountpoint: /tmp/be
        state: mounted
    
    - name: Unmount ZFS boot environment
      beadm:
        name: BE
        state: unmounted
    
    - name: Activate ZFS boot environment
      beadm:
        name: upgrade-be
        state: activated

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
        <td> state </td>
        <td> state of the target </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> force </td>
        <td> if forced action is wanted </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> name </td>
        <td> BE name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> pre-upgrade </td>
    </tr>
            <tr>
        <td> mountpoint </td>
        <td> BE mountpoint </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> /mnt/be </td>
    </tr>
            <tr>
        <td> snapshot </td>
        <td> ZFS snapshot to create BE from </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> rpool/ROOT/oi-hipster@fresh </td>
    </tr>
            <tr>
        <td> options </td>
        <td> BE additional options </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> compression=on </td>
    </tr>
            <tr>
        <td> description </td>
        <td> BE description </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> Upgrade from 9.0 to 10.0 </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
