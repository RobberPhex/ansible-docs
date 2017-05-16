.. _win_ping:


win_ping - A windows version of the classic ping module.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Checks management connectivity of a windows host




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
    <td>data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>pong</td>
        <td><ul></ul></td>
        <td><div>Alternate data to return instead of 'pong'</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Test connectivity to a windows host
    ansible winserver -m win_ping
    
    # Example from an Ansible Playbook
    - action: win_ping




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

