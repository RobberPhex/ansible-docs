.. _zabbix_maintenance:


zabbix_maintenance - Create Zabbix maintenance windows
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.8

This module will let you create Zabbix maintenance windows.

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
    <td>collect_data</td>
    <td>no</td>
    <td>true</td>
        <td><ul></ul></td>
        <td>Type of maintenance. With data collection, or without.</td>
    </tr>
            <tr>
    <td>desc</td>
    <td>yes</td>
    <td>Created by Ansible</td>
        <td><ul></ul></td>
        <td>Short description of maintenance window.</td>
    </tr>
            <tr>
    <td>host_groups</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Host groups to manage maintenance window for. Separate multiple groups with commas. <code>host_group</code> is an alias for <code>host_groups</code>. <b>Required</b> option when <code>state</code> is <em>present</em> and no <code>host_names</code> specified.</td>
    </tr>
            <tr>
    <td>host_names</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Hosts to manage maintenance window for. Separate multiple hosts with commas. <code>host_name</code> is an alias for <code>host_names</code>. <b>Required</b> option when <code>state</code> is <em>present</em> and no <code>host_groups</code> specified.</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Zabbix user password.</td>
    </tr>
            <tr>
    <td>login_user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Zabbix user name.</td>
    </tr>
            <tr>
    <td>minutes</td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td>Length of maintenance window in minutes.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Unique name of maintenance window.</td>
    </tr>
            <tr>
    <td>server_url</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url of Zabbix server, with protocol (http or https). <code>url</code> is an alias for <code>server_url</code>.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Create or remove a maintenance window.</td>
    </tr>
        </table>


.. note:: Requires zabbix-api python module


Examples
--------

.. raw:: html

    <br/>


::

    # Create maintenance window named "Update of www1"
    # for host www1.example.com for 90 minutes
    - zabbix_maintenance: name="Update of www1"
                          host_name=www1.example.com
                          state=present
                          minutes=90
                          server_url=https://monitoring.example.com
                          login_user=ansible
                          login_password=pAsSwOrD
    
    # Create maintenance window named "Mass update"
    # for host www1.example.com and host groups Office and Dev
    - zabbix_maintenance: name="Update of www1"
                          host_name=www1.example.com
                          host_groups=Office,Dev
                          state=present
                          server_url=https://monitoring.example.com
                          login_user=ansible
                          login_password=pAsSwOrD
    
    # Create maintenance window named "update"
    # for hosts www1.example.com and db1.example.com and without data collection.
    - zabbix_maintenance: name=update
                          host_names=www1.example.com,db1.example.com
                          state=present
                          collect_data=false
                          server_url=https://monitoring.example.com
                          login_user=ansible
                          login_password=pAsSwOrD
    
    # Remove maintenance window named "Test1"
    - zabbix_maintenance: name=Test1
                          state=absent
                          server_url=https://monitoring.example.com
                          login_user=ansible
                          login_password=pAsSwOrD

.. note:: Useful for setting hosts in maintenance mode before big update, and removing maintenance window after update.
.. note:: Module creates maintenance window from now() to now() + minutes, so if Zabbix server's time and host's time are not synchronized, you will get strange results.
.. note:: Install required module with 'pip install zabbix-api' command.
.. note:: Checks existance only by maintenance name.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

