.. _htpasswd:


htpasswd - manage user files for basic authentication
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Add and remove username/password entries in a password file using htpasswd.
This is used by web servers such as Apache and Nginx for basic authentication.

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
    <td>create</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Used with <code>state=present</code>. If specified, the file will be created if it does not already exist. If set to "no", will fail if the file does not exist</td>
    </tr>
            <tr>
    <td>crypt_scheme</td>
    <td>no</td>
    <td>apr_md5_crypt</td>
        <td><ul><li>apr_md5_crypt</li><li>des_crypt</li><li>ldap_sha1</li><li>plaintext</li></ul></td>
        <td>Encryption scheme to be used.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>User name to add or remove</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Password associated with user.Must be specified if user does not exist yet.</td>
    </tr>
            <tr>
    <td>path</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path to the file that contains the usernames and passwords</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether the user entry should be present or not</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Add a user to a password file and ensure permissions are set
    - htpasswd: path=/etc/nginx/passwdfile name=janedoe password=9s36?;fyNp owner=root group=www-data mode=0640
    # Remove a user from a password file
    - htpasswd: path=/etc/apache2/passwdfile name=foobar state=absent

.. note:: This module depends on the *passlib* Python library, which needs to be installed on all target systems.
.. note:: On Debian, Ubuntu, or Fedora: install *python-passlib*.
.. note:: On RHEL or CentOS: Enable EPEL, then install *python-passlib*.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

