.. _redis:


redis - Various redis commands, slave and flush
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Unified utility to interact with redis instances. 'slave' sets a redis instance in slave or master mode. 'flush' flushes all the instance or a specified db. 'config' (new in 1.6), ensures a configuration setting on an instance.


Requirements (on host that executes module)
-------------------------------------------

  * redis


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
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>slave</li><li>flush</li><li>config</li></ul></td>
        <td><div>The selected redis command</div></td></tr>
            <tr>
    <td>db<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The database to flush (used in db mode) [flush command]</div></td></tr>
            <tr>
    <td>flush_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>all</li><li>db</li></ul></td>
        <td><div>Type of flush (all the dbs in a redis instance or a specific one) [flush command]</div></td></tr>
            <tr>
    <td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>The host running the database</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password used to authenticate with (usually not used)</div></td></tr>
            <tr>
    <td>login_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>6379</td>
        <td><ul></ul></td>
        <td><div>The port to connect to</div></td></tr>
            <tr>
    <td>master_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The host of the master instance [slave command]</div></td></tr>
            <tr>
    <td>master_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The port of the master instance [slave command]</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A redis config key.</div></td></tr>
            <tr>
    <td>slave_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>slave</td>
        <td><ul><li>master</li><li>slave</li></ul></td>
        <td><div>the mode of the redis instance [slave command]</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A redis config value.</div></td></tr>
        </table>
    </br>



Examples
--------

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


Notes
-----

.. note:: Requires the redis-py Python package on the remote host. You can install it with pip (pip install redis) or with a package manager. https://github.com/andymccurdy/redis-py
.. note:: If the redis master instance we are making slave of is password protected this needs to be in the redis.conf in the masterauth variable


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

