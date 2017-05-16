.. _win_updates:


win_updates - Download and install Windows updates
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Searches, downloads, and installs Windows updates synchronously by automating the Windows Update client




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
    <td>category_names<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'CriticalUpdates', u'SecurityUpdates', u'UpdateRollups']</td>
        <td><ul><li>Application</li><li>Connectors</li><li>CriticalUpdates</li><li>DefinitionUpdates</li><li>DeveloperKits</li><li>FeaturePacks</li><li>Guidance</li><li>SecurityUpdates</li><li>ServicePacks</li><li>Tools</li><li>UpdateRollups</li><li>Updates</li></ul></td>
        <td><div>A scalar or list of categories to install updates from</div></td></tr>
            <tr>
    <td>log_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set, win_updates will append update progress to the specified file. The directory must already exist.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>installed</td>
        <td><ul><li>installed</li><li>searched</li></ul></td>
        <td><div>Controls whether found updates are returned as a list or actually installed.</div><div>This module also supports Ansible check mode, which has the same effect as setting state=searched</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

        # Install all security, critical, and rollup updates
        win_updates:
            category_names: ['SecurityUpdates','CriticalUpdates','UpdateRollups']
    
        # Install only security updates
        win_updates: category_names=SecurityUpdates
    
        # Search-only, return list of found updates (if any), log to c:nsible_wu.txt
        win_updates: category_names=SecurityUpdates state=searched log_path=c:/ansible_wu.txt

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
        <td> installed_update_count </td>
        <td> The number of updates successfully installed </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 2 </td>
    </tr>
            <tr>
        <td> reboot_required </td>
        <td> True when the target server requires a reboot to complete updates (no further updates can be installed until after a reboot) </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> failed_update_count </td>
        <td> The number of updates that failed to install </td>
        <td align=center> always </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
    </tr>
            <tr>
        <td> found_update_count </td>
        <td> The number of updates found needing to be applied </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 3 </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> List of updates that were found/installed </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center> None </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> kb </td>
        <td> A list of KB article IDs that apply to the update </td>
        <td align=center> always </td>
        <td align=center> list of strings </td>
        <td align=center> ['3004365'] </td>
        </tr>
                <tr>
        <td> title </td>
        <td> Display name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> Security Update for Windows Server 2012 R2 (KB3004365) </td>
        </tr>
                <tr>
        <td> failure_hresult_code </td>
        <td> The HRESULT code from a failed update </td>
        <td align=center> on install failure </td>
        <td align=center> boolean </td>
        <td align=center> 2147942402 </td>
        </tr>
                <tr>
        <td> id </td>
        <td> Internal Windows Update GUID </td>
        <td align=center> always </td>
        <td align=center> string (guid) </td>
        <td align=center> fb95c1c8-de23-4089-ae29-fd3351d55421 </td>
        </tr>
                <tr>
        <td> installed </td>
        <td> Was the update successfully installed </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note:: win_updates must be run by a user with membership in the local Administrators group
.. note:: win_updates will use the default update service configured for the machine (Windows Update, Microsoft Update, WSUS, etc)
.. note:: win_updates does not manage reboots, but will signal when a reboot is required with the reboot_required return value.
.. note:: win_updates can take a significant amount of time to complete (hours, in some cases). Performance depends on many factors, including OS version, number of updates, system load, and update server load.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

