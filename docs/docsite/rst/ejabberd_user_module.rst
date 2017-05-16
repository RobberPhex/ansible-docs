.. _ejabberd_user:


ejabberd_user - Manages users for ejabberd servers
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module provides user management for ejabberd servers


Requirements (on host that executes module)
-------------------------------------------

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
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the ejabberd host associated with this username</div>        </td></tr>
                <tr><td>logging<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li><li>yes</li><li>no</li></ul></td>
        <td><div>enables or disables the local syslog facility for this module</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the password to assign to the username</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>describe the desired state of the user to be managed</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the name of the user to manage</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example playbook entries using the ejabberd_user module to manage users state.
    
    - name: create a user if it does not exists
      ejabberd_user:
        username: test
        host: server
        password: password
    
    - name: delete a user if it exists
      ejabberd_user:
        username: test
        host: server
        state: absent


Notes
-----

.. note::
    - Password parameter is required for state == present only
    - Passwords must be stored in clear text for this release
    - The ejabberd configuration file must include mod_admin_extra as a module.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
