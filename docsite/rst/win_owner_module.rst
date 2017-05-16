.. _win_owner:


win_owner - Set owner
+++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Set owner of files or directories




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
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to be used for changing owner</div></td></tr>
            <tr>
    <td>recurse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>False</li><li>True</li></ul></td>
        <td><div>Indicates if the owner should be changed recursively</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name to be used for changing owner</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Playbook example
    ---
    - name: Change owner of Path
      win_owner:
        path: 'C:\apache\'
        user: apache
        recurse: yes
    
    - name: Set the owner of root directory
      win_owner:
        path: 'C:\apache\'
        user: SYSTEM
        recurse: no




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

