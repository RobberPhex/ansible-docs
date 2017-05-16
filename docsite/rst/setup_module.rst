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
    <td>fact_path</td>
    <td>no</td>
    <td>/etc/ansible/facts.d</td>
        <td><ul></ul></td>
        <td>path used for local ansible facts (*.fact) - files in this dir will be run (if executable) and their results be added to ansible_local facts if a file is not executable it is read. File/results format can be json or ini-format (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>filter</td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td>if supplied, only return facts that match this shell-style (fnmatch) wildcard. (added in Ansible 1.1)</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Display facts from all hosts and store them indexed by I(hostname) at C(/tmp/facts).
    ansible all -m setup --tree /tmp/facts
    
    # Display only facts regarding memory found by ansible on all hosts and output them.
    ansible all -m setup -a 'filter=ansible_*_mb'
    
    # Display only facts returned by facter.
    ansible all -m setup -a 'filter=facter_*'
    
    # Display only facts about certain interfaces.
    ansible all -m setup -a 'filter=ansible_eth[0-2]'

.. note:: More ansible facts will be added with successive releases. If *facter* or *ohai* are installed, variables from these programs will also be snapshotted into the JSON file for usage in templating. These variables are prefixed with ``facter_`` and ``ohai_`` so it's easy to tell their source. All variables are bubbled up to the caller. Using the ansible facts and choosing to not install *facter* and *ohai* means you can avoid Ruby-dependencies on your remote systems. (See also ``facter`` and ``ohai``.)
.. note:: The filter option filters only the first level subkey below ansible_facts.
.. note:: If the target host is Windows, you will not currently have the ability to use ``fact_path`` or ``filter`` as this is provided by a simpler implementation of the module. Different facts are returned for Windows hosts.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

