.. _setup:


setup - Gathers facts about remote hosts
++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module is automatically called by playbooks to gather useful variables about remote hosts that can be used in playbooks. It can also be executed directly by ``/usr/bin/ansible`` to check what variables are available to a host. Ansible provides many *facts* about the system, automatically.




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
    <td>fact_path<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>/etc/ansible/facts.d</td>
        <td><ul></ul></td>
        <td><div>path used for local ansible facts (*.fact) - files in this dir will be run (if executable) and their results be added to ansible_local facts if a file is not executable it is read. File/results format can be json or ini-format</div></td></tr>
            <tr>
    <td>filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td><div>if supplied, only return facts that match this shell-style (fnmatch) wildcard.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Display facts from all hosts and store them indexed by I(hostname) at C(/tmp/facts).
    ansible all -m setup --tree /tmp/facts
    
    # Display only facts regarding memory found by ansible on all hosts and output them.
    ansible all -m setup -a 'filter=ansible_*_mb'
    
    # Display only facts returned by facter.
    ansible all -m setup -a 'filter=facter_*'
    
    # Display only facts about certain interfaces.
    ansible all -m setup -a 'filter=ansible_eth[0-2]'


Notes
-----

.. note:: More ansible facts will be added with successive releases. If *facter* or *ohai* are installed, variables from these programs will also be snapshotted into the JSON file for usage in templating. These variables are prefixed with ``facter_`` and ``ohai_`` so it's easy to tell their source. All variables are bubbled up to the caller. Using the ansible facts and choosing to not install *facter* and *ohai* means you can avoid Ruby-dependencies on your remote systems. (See also :ref:`facter <facter>` and :ref:`ohai <ohai>`.)
.. note:: The filter option filters only the first level subkey below ansible_facts.
.. note:: If the target host is Windows, you will not currently have the ability to use ``fact_path`` or ``filter`` as this is provided by a simpler implementation of the module. Different facts are returned for Windows hosts.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

