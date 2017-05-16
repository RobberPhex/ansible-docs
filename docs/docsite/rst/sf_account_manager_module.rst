.. _sf_account_manager:


sf_account_manager - Manage SolidFire accounts
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, destroy, or update accounts on SolidFire


Requirements (on host that executes module)
-------------------------------------------

  * solidfire-sdk-python (1.1.0.92)


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
                <tr><td>account_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The ID of the account to manage or update.</div>        </td></tr>
                <tr><td>attributes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of Name/Value pairs in JSON object format.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the SolidFire cluster.</div>        </td></tr>
                <tr><td>initiator_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>CHAP secret to use for the initiator. Should be 12-16 characters long and impenetrable.</div><div>The CHAP initiator secrets must be unique and cannot be the same as the target CHAP secret.</div><div>If not specified, a random secret is created.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Unique username for this account. (May be 1 to 64 characters in length).</div>        </td></tr>
                <tr><td>new_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>New name for the user account.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified account should exist or not.</div>        </td></tr>
                <tr><td>status<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Status of the account.</div>        </td></tr>
                <tr><td>target_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>CHAP secret to use for the target (mutual CHAP authentication).</div><div>Should be 12-16 characters long and impenetrable.</div><div>The CHAP target secrets must be unique and cannot be the same as the initiator CHAP secret.</div><div>If not specified, a random secret is created.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Please ensure that the user has the adequate permissions. For more information, please read the official documentation <a href='https://goo.gl/ddJa4Q'>https://goo.gl/ddJa4Q</a>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create Account
      sf_account_manager:
        hostname: "{{ solidfire_hostname }}"
        username: "{{ solidfire_username }}"
        password: "{{ solidfire_password }}"
        state: present
        name: TenantA
    
    - name: Modify Account
      sf_account_manager:
        hostname: "{{ solidfire_hostname }}"
        username: "{{ solidfire_username }}"
        password: "{{ solidfire_password }}"
        state: present
        name: TenantA
        new_name: TenantA-Renamed
    
    - name: Delete Account
      sf_account_manager:
        hostname: "{{ solidfire_hostname }}"
        username: "{{ solidfire_username }}"
        password: "{{ solidfire_password }}"
        state: absent
        name: TenantA-Renamed


Notes
-----

.. note::
    - The modules prefixed with ``sf\_`` are built to support the SolidFire storage platform.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
