.. _win_environment:


win_environment - Modifies environment variables on windows hosts.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Uses .net Environment to set or remove environment variables and can set at User, Machine or Process level.
User level environment variables will be set, but not available until the user has logged off and on again.




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
    <td>level<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>no default</td>
        <td><ul><li>machine</li><li>process</li><li>user</li></ul></td>
        <td><div>The level at which to set the environment variable.</div><div>Use 'machine' to set for all users.</div><div>Use 'user' to set for the current user that ansible is connected as.</div><div>Use 'process' to set for the current process.  Probably not that useful.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>no default</td>
        <td><ul></ul></td>
        <td><div>The name of the environment variable</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>present to ensure environment variable is set, or absent to ensure it is removed</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no default</td>
        <td><ul></ul></td>
        <td><div>The value to store in the environment variable. Can be omitted for state=absent</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Set an environment variable for all users
      win_environment:
        state: present
        name: TestVariable
        value: "Test value"
        level: machine
      # Remove an environment variable for the current users
      win_environment:
        state: absent
        name: TestVariable
        level: user


Notes
-----

.. note:: This module does not broadcast change events. This means that the minority of windows applications which can have their environment changed without restarting will not be notified and therefore will need restarting to pick up new environment settings. User level environment variables will require the user to log out and in again before they become available.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

