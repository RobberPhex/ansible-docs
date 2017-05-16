.. _ejabberd_user:


ejabberd_user - Manages users for ejabberd servers
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module provides user management for ejabberd servers


Requirements
------------

  * ejabberd with mod_admin_extra


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
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the ejabberd host associated with this username</div></td></tr>
            <tr>
    <td>logging<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li><li>yes</li><li>no</li></ul></td>
        <td><div>enables or disables the local syslog facility for this module</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the password to assign to the username</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>describe the desired state of the user to be managed</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the name of the user to manage</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    Example playbook entries using the ejabberd_user module to manage users state.
    
        tasks:
    
        - name: create a user if it does not exists
          action: ejabberd_user username=test host=server password=password
    
        - name: delete a user if it exists
          action: ejabberd_user username=test host=server state=absent


Notes
-----

.. note:: Password parameter is required for state == present only
.. note:: Passwords must be stored in clear text for this release
.. note:: The ejabberd configuration file must include mod_admin_extra as a module.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

