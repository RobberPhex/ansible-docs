.. _redis:


redis - Various redis commands, slave and flush
+++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Unified utility to interact with redis instances. 'slave' sets a redis instance in slave or master mode. 'flush' flushes all the instance or a specified db. 'config' (new in 1.6), ensures a configuration setting on an instance.

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
    <td>command</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>slave</li><li>flush</li><li>config</li></ul></td>
        <td>The selected redis command</td>
    </tr>
            <tr>
    <td>db</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The database to flush (used in db mode) [flush command]</td>
    </tr>
            <tr>
    <td>flush_mode</td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>all</li><li>db</li></ul></td>
        <td>Type of flush (all the dbs in a redis instance or a specific one) [flush command]</td>
    </tr>
            <tr>
    <td>login_host</td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td>The host running the database</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The password used to authenticate with (usually not used)</td>
    </tr>
            <tr>
    <td>login_port</td>
    <td>no</td>
    <td>6379</td>
        <td><ul></ul></td>
        <td>The port to connect to</td>
    </tr>
            <tr>
    <td>master_host</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The host of the master instance [slave command]</td>
    </tr>
            <tr>
    <td>master_port</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The port of the master instance [slave command]</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A redis config key. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>slave_mode</td>
    <td>no</td>
    <td>slave</td>
        <td><ul><li>master</li><li>slave</li></ul></td>
        <td>the mode of the redis instance [slave command]</td>
    </tr>
            <tr>
    <td>value</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A redis config value. (added in Ansible 1.6)</td>
    </tr>
        </table>


.. note:: Requires redis


Examples
--------

.. raw:: html

    <br/>


::

    # Set local redis instance to be slave of melee.island on port 6377
    - redis: command=slave master_host=melee.island master_port=6377
    
    # Deactivate slave mode
    - redis: command=slave slave_mode=master
    
    # Flush all the redis db
    - redis: command=flush flush_mode=all
    
    # Flush only one db in a redis instance
    - redis: command=flush db=1 flush_mode=db
    
    # Configure local redis to have 10000 max clients
    - redis: command=config name=maxclients value=10000
    
    # Configure local redis to have lua time limit of 100 ms
    - redis: command=config name=lua-time-limit value=100

.. note:: Requires the redis-py Python package on the remote host. You can install it with pip (pip install redis) or with a package manager. https://github.com/andymccurdy/redis-py
.. note:: If the redis master instance we are making slave of is password protected this needs to be in the redis.conf in the masterauth variable


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

