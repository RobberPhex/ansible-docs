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
    <td>groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The groups to add the hostname to, comma separated.</div></br>
        <div style="font-size: small;">aliases: groupname, group<div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hostname/ip of the host to add to the inventory, can include a colon and a port number.</div></br>
        <div style="font-size: small;">aliases: hostname, host<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # add host to group 'just_created' with variable foo=42
    - add_host: name={{ ip_from_ec2 }} groups=just_created foo=42
    
    # add a host with a non-standard port local to your machines
    - add_host: name={{ new_ip }}:{{ new_port }}
    
    # add a host alias that we reach through a tunnel
    - add_host: hostname={{ new_ip }}
                ansible_ssh_host={{ inventory_hostname }}
                ansible_ssh_port={{ new_port }}


Notes
-----

.. note:: This module bypasses the play host loop and only runs once for all the hosts in the play, if you need it to iterate use a with\_ directive.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

