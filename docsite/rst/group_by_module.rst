.. _group_by:


group_by - Create Ansible groups based on facts
+++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Use facts to create ad-hoc groups that can be used later in a playbook.




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
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The variables whose values will be used as groups</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create groups based on the machine architecture
    -  group_by: key=machine_{{ ansible_machine }}
    # Create groups like 'kvm-host'
    -  group_by: key=virt_{{ ansible_virtualization_type }}_{{ ansible_virtualization_role }}


Notes
-----

.. note:: Spaces in group names are converted to dashes '-'.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

