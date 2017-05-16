.. _win_share:


win_share - Manage Windows shares
+++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add, modify or remove Windows share and set share permissions.


Requirements (on host that executes module)
-------------------------------------------

  * Windows 8.1 / Windows 2012 or newer


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
    <td>change<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>Specify user list that should get read and write access on share, separated by comma.</div></td></tr>
            <tr>
    <td>deny<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>Specify user list that should get no access, regardless of implied access on share, separated by comma.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>Share description</div></td></tr>
            <tr>
    <td>full<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>Specify user list that should get full access on share, separated by comma.</div></td></tr>
            <tr>
    <td>list<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Specify whether to allow or deny file listing, in case user got no permission on share</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Share name</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Share directory</div></td></tr>
            <tr>
    <td>read<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>Specify user list that should get read access on share, separated by comma.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specify whether to add <code>present</code> or remove <code>absent</code> the specified share</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Playbook example
    # Add share and set permissions
    ---
    - name: Add secret share
      win_share:
        name: internal
        description: top secret share
        path: C:/shares/internal
        list: 'no'
        full: Administrators,CEO
        read: HR-Global
        deny: HR-External
    
    - name: Add public company share
      win_share:
        name: company
        description: top secret share
        path: C:/shares/company
        list: 'yes'
        full: Administrators,CEO
        read: Global
    
    # Remove previously added share
      win_share:
        name: internal
        state: absent




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

