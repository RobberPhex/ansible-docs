.. _mysql_replication:


mysql_replication - Manage MySQL replication
++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Manages MySQL server replication, slave, master status get and change master host.

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
    <td>master_connect_retry</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_host</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_log_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_log_pos</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_port</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_ssl</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_ssl_ca</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_ssl_capath</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_ssl_cert</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_ssl_cipher</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_ssl_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>master_user</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>mode</td>
    <td>no</td>
    <td>getslave</td>
        <td><ul><li>getslave</li><li>getmaster</li><li>changemaster</li><li>stopslave</li><li>startslave</li></ul></td>
        <td>module operating mode. Could be getslave (SHOW SLAVE STATUS), getmaster (SHOW MASTER STATUS), changemaster (CHANGE MASTER TO), startslave (START SLAVE), stopslave (STOP SLAVE)</td>
    </tr>
            <tr>
    <td>relay_log_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
            <tr>
    <td>relay_log_pos</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>same as mysql variable</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Stop mysql slave thread
    - mysql_replication: mode=stopslave
    
    # Get master binlog file name and binlog position
    - mysql_replication: mode=getmaster
    
    # Change master to master server 192.168.1.1 and use binary log 'mysql-bin.000009' with position 4578
    - mysql_replication: mode=changemaster master_host=192.168.1.1 master_log_file=mysql-bin.000009 master_log_pos=4578



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

