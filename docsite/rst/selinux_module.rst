.. _selinux:


selinux - Change policy and state of SELinux
++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Configures the SELinux mode and policy. A reboot may be required after usage. Ansible will not issue this reboot but will let you know when it is required.

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
    <td>conf</td>
    <td>no</td>
    <td>/etc/selinux/config</td>
        <td><ul></ul></td>
        <td>path to the SELinux configuration file, if non-standard</td>
    </tr>
            <tr>
    <td>policy</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the SELinux policy to use (example: <code>targeted</code>) will be required if state is not <code>disabled</code></td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>enforcing</li><li>permissive</li><li>disabled</li></ul></td>
        <td>The SELinux mode</td>
    </tr>
        </table>


.. note:: Requires libselinux-python


Examples
--------

.. raw:: html

    <br/>


::

    - selinux: policy=targeted state=enforcing
    - selinux: policy=targeted state=permissive
    - selinux: state=disabled

.. note:: Not tested on any debian based system


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

