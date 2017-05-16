.. _win_ping:


win_ping - A windows version of the classic ping module.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Checks management connectivity of a windows host




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
                <tr><td>data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>pong</td>
        <td></td>
        <td><div>Alternate data to return instead of 'pong'</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Test connectivity to a windows host
    # ansible winserver -m win_ping
    
    # Example from an Ansible Playbook
    - win_ping:
    
    # Induce a crash to see what happens
    - win_ping:
        data: crash





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
