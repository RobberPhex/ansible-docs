.. _win_user:


win_user - Manages local Windows user accounts
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages local Windows user accounts




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
                <tr><td>account_disabled<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div><code>yes</code> will disable the user account.  <code>no</code> will clear the disabled flag.</div>        </td></tr>
                <tr><td>account_locked<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>no</li></ul></td>
        <td><div><code>no</code> will unlock the user account if locked.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of the user</div>        </td></tr>
                <tr><td>fullname<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Full name of the user</div>        </td></tr>
                <tr><td>groups<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Adds or removes the user from this comma-separated lis of groups, depending on the value of <em>groups_action</em>. When <em>groups_action</em> is <code>replace</code> and <em>groups</em> is set to the empty string ('groups='), the user is removed from all groups.</div>        </td></tr>
                <tr><td>groups_action<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>replace</td>
        <td><ul><li>replace</li><li>add</li><li>remove</li></ul></td>
        <td><div>If <code>replace</code>, the user is added as a member of each group in <em>groups</em> and removed from any other groups.  If <code>add</code>, the user is added to each group in <em>groups</em> where not already a member.  If <code>remove</code>, the user is removed from each group in <em>groups</em>.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the user to create, remove or modify.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Optionally set the user's password to this (plain text) value.</div>        </td></tr>
                <tr><td>password_expired<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div><code>yes</code> will require the user to change their password at next login. <code>no</code> will clear the expired password flag.</div>        </td></tr>
                <tr><td>password_never_expires<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div><code>yes</code> will set the password to never expire.  <code>no</code> will allow the password to expire.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>query</li></ul></td>
        <td><div>When <code>present</code>, creates or updates the user account.  When <code>absent</code>, removes the user account if it exists.  When <code>query</code> (new in 1.9), retrieves the user account details without making any changes.</div>        </td></tr>
                <tr><td>update_password<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>always</td>
        <td><ul><li>always</li><li>on_create</li></ul></td>
        <td><div><code>always</code> will update passwords if they differ.  <code>on_create</code> will only set the password for newly created users.</div>        </td></tr>
                <tr><td>user_cannot_change_password<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div><code>yes</code> will prevent the user from changing their password.  <code>no</code> will allow the user to change their password.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Ensure user bob is present
      win_user:
        name: bob
        password: B0bP4ssw0rd
        state: present
        groups:
          - Users
    
    - name: Ensure user bob is absent
      win_user:
        name: bob
        state: absent





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
