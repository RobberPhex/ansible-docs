.. _htpasswd:


htpasswd - manage user files for basic authentication
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

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
    <td>create<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Used with <code>state=present</code>. If specified, the file will be created if it does not already exist. If set to "no", will fail if the file does not exist</div></td></tr>
            <tr>
    <td>crypt_scheme<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>apr_md5_crypt</td>
        <td><ul><li>apr_md5_crypt</li><li>des_crypt</li><li>ldap_sha1</li><li>plaintext</li></ul></td>
        <td><div>Encryption scheme to be used.  As well as the four choices listed here, you can also use any other hash supported by passlib, such as md5_crypt and sha256_crypt, which are linux passwd hashes.  If you do so the password file will not be compatible with Apache or Nginx</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>User name to add or remove</div></br>
        <div style="font-size: small;">aliases: username<div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password associated with user.</div><div>Must be specified if user does not exist yet.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the file that contains the usernames and passwords</div></br>
        <div style="font-size: small;">aliases: dest, destfile<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the user entry should be present or not</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add a user to a password file and ensure permissions are set
    - htpasswd: path=/etc/nginx/passwdfile name=janedoe password=9s36?;fyNp owner=root group=www-data mode=0640
    # Remove a user from a password file
    - htpasswd: path=/etc/apache2/passwdfile name=foobar state=absent
    # Add a user to a password file suitable for use by libpam-pwdfile
    - htpasswd: path=/etc/mail/passwords name=alex password=oedu2eGh crypt_scheme=md5_crypt


Notes
-----

.. note:: This module depends on the *passlib* Python library, which needs to be installed on all target systems.
.. note:: On Debian, Ubuntu, or Fedora: install *python-passlib*.
.. note:: On RHEL or CentOS: Enable EPEL, then install *python-passlib*.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

