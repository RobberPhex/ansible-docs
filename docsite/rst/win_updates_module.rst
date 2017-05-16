.. _win_updates:


win_updates - Download and install Windows updates
++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 2.0

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
    <td>category_names</td>
    <td>no</td>
    <td>['CriticalUpdates', 'SecurityUpdates', 'UpdateRollups']</td>
        <td><ul><li>Application</li><li>Connectors</li><li>CriticalUpdates</li><li>DefinitionUpdates</li><li>DeveloperKits</li><li>FeaturePacks</li><li>Guidance</li><li>SecurityUpdates</li><li>ServicePacks</li><li>Tools</li><li>UpdateRollups</li><li>Updates</li></ul></td>
        <td>A scalar or list of categories to install updates from</td>
    </tr>
            <tr>
    <td>log_path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If set, win_updates will append update progress to the specified file. The directory must already exist.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>installed</td>
        <td><ul><li>installed</li><li>searched</li></ul></td>
        <td>Controls whether found updates are returned as a list or actually installed.This module also supports Ansible check mode, which has the same effect as setting state=searched</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

        # Install all security, critical, and rollup updates
        win_updates:
            category_names: ['SecurityUpdates','CriticalUpdates','UpdateRollups']
    
        # Install only security updates
        win_updates: category_names=SecurityUpdates
    
        # Search-only, return list of found updates (if any), log to c:nsible_wu.txt
        win_updates: category_names=SecurityUpdates status=searched log_path=c:/ansible_wu.txt

.. note:: win_updates must be run by a user with membership in the local Administrators group
.. note:: win_updates will use the default update service configured for the machine (Windows Update, Microsoft Update, WSUS, etc)
.. note:: win_updates does not manage reboots, but will signal when a reboot is required with the reboot_required return value.
.. note:: win_updates can take a significant amount of time to complete (hours, in some cases). Performance depends on many factors, including OS version, number of updates, system load, and update server load.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

