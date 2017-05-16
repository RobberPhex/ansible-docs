.. _mysql_variables:


mysql_variables - Manage MySQL global variables
+++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Query / Set MySQL variables

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
    <td>login_host</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>mysql host to connect</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>password to connect mysql host, if defined login_user also needed.</td>
    </tr>
            <tr>
    <td>login_unix_socket</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>unix socket to connect mysql server</td>
    </tr>
            <tr>
    <td>login_user</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>username to connect mysql host, if defined login_password also needed.</td>
    </tr>
            <tr>
    <td>value</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If set, then sets variable value to this</td>
    </tr>
            <tr>
    <td>variable</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Variable name to operate</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Check for sync_binlog setting
    - mysql_variables: variable=sync_binlog
    
    # Set read_only variable to 1
    - mysql_variables: variable=read_only value=1



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

