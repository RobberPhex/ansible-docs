.. _setup:


setup - Gathers facts about remote hosts
++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module is automatically called by playbooks to gather useful variables about remote hosts that can be used in playbooks. It can also be executed directly by ``/usr/bin/ansible`` to check what variables are available to a host. Ansible provides many *facts* about the system, automatically.




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
                <tr><td>fact_path<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>/etc/ansible/facts.d</td>
        <td></td>
        <td><div>path used for local ansible facts (*.fact) - files in this dir will be run (if executable) and their results be added to ansible_local facts if a file is not executable it is read. Check notes for Windows options. (from 2.1 on) File/results format can be json or ini-format</div>        </td></tr>
                <tr><td>filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td></td>
        <td><div>if supplied, only return facts that match this shell-style (fnmatch) wildcard.</div>        </td></tr>
                <tr><td>gather_subset<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>all</td>
        <td></td>
        <td><div>if supplied, restrict the additional facts collected to the given subset. Possible values: all, hardware, network, virtual, ohai, and facter Can specify a list of values to specify a larger subset. Values can also be used with an initial <code>!</code> to specify that that specific subset should not be collected.  For instance: !hardware, !network, !virtual, !ohai, !facter.  Note that a few facts are always collected.  Use the filter parameter if you do not want to display those.</div>        </td></tr>
                <tr><td>gather_timeout<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Set the default timeout in seconds for individual fact gathering</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Display facts from all hosts and store them indexed by I(hostname) at C(/tmp/facts).
    # ansible all -m setup --tree /tmp/facts
    
    # Display only facts regarding memory found by ansible on all hosts and output them.
    # ansible all -m setup -a 'filter=ansible_*_mb'
    
    # Display only facts returned by facter.
    # ansible all -m setup -a 'filter=facter_*'
    
    # Display only facts about certain interfaces.
    # ansible all -m setup -a 'filter=ansible_eth[0-2]'
    
    # Restrict additional gathered facts to network and virtual.
    # ansible all -m setup -a 'gather_subset=network,virtual'
    
    # Do not call puppet facter or ohai even if present.
    # ansible all -m setup -a 'gather_subset=!facter,!ohai'
    
    # Only collect the minimum amount of facts:
    # ansible all -m setup -a 'gather_subset=!all'
    
    # Display facts from Windows hosts with custom facts stored in C(C:\custom_facts).
    # ansible windows -m setup -a "fact_path='c:\custom_facts'"


Notes
-----

.. note::
    - More ansible facts will be added with successive releases. If *facter* or *ohai* are installed, variables from these programs will also be snapshotted into the JSON file for usage in templating. These variables are prefixed with ``facter_`` and ``ohai_`` so it's easy to tell their source. All variables are bubbled up to the caller. Using the ansible facts and choosing to not install *facter* and *ohai* means you can avoid Ruby-dependencies on your remote systems. (See also :ref:`facter <facter>` and :ref:`ohai <ohai>`.)
    - The filter option filters only the first level subkey below ansible_facts.
    - If the target host is Windows, you will not currently have the ability to use ``filter`` as this is provided by a simpler implementation of the module.
    - If the target host is Windows you can now use ``fact_path``. Make sure that this path exists on the target host. Files in this path MUST be PowerShell scripts (``*.ps1``) and their output must be formattable in JSON (Ansible will take care of this). Test the output of your scripts. This option was added in Ansible 2.1.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
