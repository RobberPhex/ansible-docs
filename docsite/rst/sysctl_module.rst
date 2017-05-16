.. _sysctl:


sysctl - Manage entries in sysctl.conf.
+++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.0

This module manipulates sysctl entries and optionally performs a ``/sbin/sysctl -p`` after changing them.

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
    <td>ignoreerrors</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Use this option to ignore errors about unknown keys.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The dot-separated path (aka <em>key</em>) specifying the sysctl variable.</td>
    </tr>
            <tr>
    <td>reload</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>yes</code>, performs a <em>/sbin/sysctl -p</em> if the <code>sysctl_file</code> is updated. If <code>no</code>, does not reload <em>sysctl</em> even if the <code>sysctl_file</code> is updated.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether the entry should be present or absent in the sysctl file.</td>
    </tr>
            <tr>
    <td>sysctl_file</td>
    <td>no</td>
    <td>/etc/sysctl.conf</td>
        <td><ul></ul></td>
        <td>Specifies the absolute path to <code>sysctl.conf</code>, if not <code>/etc/sysctl.conf</code>.</td>
    </tr>
            <tr>
    <td>sysctl_set</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Verify token value with the sysctl command and set with -w if necessary (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>value</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Desired value of the sysctl key.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Set vm.swappiness to 5 in /etc/sysctl.conf
    - sysctl: name=vm.swappiness value=5 state=present
    
    # Remove kernel.panic entry from /etc/sysctl.conf
    - sysctl: name=kernel.panic state=absent sysctl_file=/etc/sysctl.conf
    
    # Set kernel.panic to 3 in /tmp/test_sysctl.conf
    - sysctl: name=kernel.panic value=3 sysctl_file=/tmp/test_sysctl.conf reload=no
    
    # Set ip forwarding on in /proc and do not reload the sysctl file
    - sysctl: name="net.ipv4.ip_forward" value=1 sysctl_set=yes
    
    # Set ip forwarding on in /proc and in the sysctl file and reload if necessary
    - sysctl: name="net.ipv4.ip_forward" value=1 sysctl_set=yes state=present reload=yes



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

