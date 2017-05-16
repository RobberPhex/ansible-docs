.. _add_host:


add_host - add a host (and alternatively a group) to the ansible-playbook in-memory inventory
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Use variables to create new hosts and groups in inventory for use in later plays of the same playbook. Takes variables so you can define the new hosts more fully.

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
    <td>groups</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The groups to add the hostname to, comma separated.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The hostname/ip of the host to add to the inventory, can include a colon and a port number.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # add host to group 'just_created' with variable foo=42
    - add_host: name={{ ip_from_ec2 }} groups=just_created foo=42
    
    # add a host with a non-standard port local to your machines
    - add_host: name={{ new_ip }}:{{ new_port }}
    
    # add a host alias that we reach through a tunnel
    - add_host: hostname={{ new_ip }}
                ansible_ssh_host={{ inventory_hostname }}
                ansible_ssh_port={{ new_port }}



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

