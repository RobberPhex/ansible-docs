.. _win_user:


win_user - Manages local Windows user accounts
++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.7

Manages local Windows user accounts

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
    <td>account_disabled</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><code>yes</code> will disable the user account.  <code>no</code> will clear the disabled flag. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>account_locked</td>
    <td>no</td>
    <td></td>
        <td><ul><li>no</li></ul></td>
        <td><code>no</code> will unlock the user account if locked. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Description of the user (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>fullname</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Full name of the user (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>groups</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Adds or removes the user from this comma-separated lis of groups, depending on the value of <em>groups_action</em>. When <em>groups_action</em> is <code>replace</code> and <em>groups</em> is set to the empty string ('groups='), the user is removed from all groups. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>groups_action</td>
    <td>no</td>
    <td>replace</td>
        <td><ul><li>replace</li><li>add</li><li>remove</li></ul></td>
        <td>If <code>replace</code>, the user is added as a member of each group in <em>groups</em> and removed from any other groups.  If <code>add</code>, the user is added to each group in <em>groups</em> where not already a member.  If <code>remove</code>, the user is removed from each group in <em>groups</em>. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the user to create, remove or modify.</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optionally set the user's password to this (plain text) value.</td>
    </tr>
            <tr>
    <td>password_expired</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><code>yes</code> will require the user to change their password at next login. <code>no</code> will clear the expired password flag. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>password_never_expires</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><code>yes</code> will set the password to never expire.  <code>no</code> will allow the password to expire. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>query</li></ul></td>
        <td>When <code>present</code>, creates or updates the user account.  When <code>absent</code>, removes the user account if it exists.  When <code>query</code> (new in 1.9), retrieves the user account details without making any changes.</td>
    </tr>
            <tr>
    <td>update_password</td>
    <td>no</td>
    <td>always</td>
        <td><ul><li>always</li><li>on_create</li></ul></td>
        <td><code>always</code> will update passwords if they differ.  <code>on_create</code> will only set the password for newly created users. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>user_cannot_change_password</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><code>yes</code> will prevent the user from changing their password.  <code>no</code> will allow the user to change their password. (added in Ansible 1.9)</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Ad-hoc example
    $ ansible -i hosts -m win_user -a "name=bob password=Password12345 groups=Users" all
    $ ansible -i hosts -m win_user -a "name=bob state=absent" all
    
    # Playbook example
    ---
    - name: Add a user
      hosts: all
      gather_facts: false
      tasks:
        - name: Add User
          win_user:
            name: ansible
            password: "@ns1bl3"
            groups: ["Users"]



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

