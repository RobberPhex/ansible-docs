.. _wait_for:


wait_for - Waits for a condition before continuing.
+++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

You can wait for a set amount of time ``timeout``, this is the default if nothing is specified.
Waiting for a port to become available is useful for when services are not immediately available after their init scripts return which is true of certain Java application servers. It is also useful when starting guests with the :ref:`virt <virt>` module and needing to pause until they are ready.
This module can also be used to wait for a regex match a string to be present in a file.
In 1.6 and later, this module can also be used to wait for a file to be available or absent on the filesystem.
In 1.8 and later, this module can also be used to wait for active connections to be closed before continuing, useful if a node is being rotated out of a load balancer pool.




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
    <td>connect_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td><div>maximum number of seconds to wait for a connection to happen before closing and retrying</div></td></tr>
            <tr>
    <td>delay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>number of seconds to wait before starting to poll</div></td></tr>
            <tr>
    <td>exclude_hosts<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>list of hosts or IPs to ignore when looking for active TCP connections for <code>drained</code> state</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>127.0.0.1</td>
        <td><ul></ul></td>
        <td><div>A resolvable hostname or IP address to wait for</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to a file on the filesytem that must exist before continuing</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>port number to poll</div></td></tr>
            <tr>
    <td>search_regex<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Can be used to match a string in either a file or a socket connection. Defaults to a multiline regex.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>present</li><li>started</li><li>stopped</li><li>absent</li><li>drained</li></ul></td>
        <td><div>either <code>present</code>, <code>started</code>, or <code>stopped</code>, <code>absent</code>, or <code>drained</code></div><div>When checking a port <code>started</code> will ensure the port is open, <code>stopped</code> will check that it is closed, <code>drained</code> will check for active connections</div><div>When checking for a file or a search string <code>present</code> or <code>started</code> will ensure that the file or string is present before continuing, <code>absent</code> will check that file is absent or removed</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td><div>maximum number of seconds to wait for</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # wait 300 seconds for port 8000 to become open on the host, don't start checking for 10 seconds
    - wait_for: port=8000 delay=10
    
    # wait 300 seconds for port 8000 of any IP to close active connections, don't start checking for 10 seconds
    - wait_for: host=0.0.0.0 port=8000 delay=10 state=drained
    
    # wait 300 seconds for port 8000 of any IP to close active connections, ignoring connections for specified hosts
    - wait_for: host=0.0.0.0 port=8000 state=drained exclude_hosts=10.2.1.2,10.2.1.3
    
    # wait until the file /tmp/foo is present before continuing
    - wait_for: path=/tmp/foo
    
    # wait until the string "completed" is in the file /tmp/foo before continuing
    - wait_for: path=/tmp/foo search_regex=completed
    
    # wait until the lock file is removed
    - wait_for: path=/var/lock/file.lock state=absent
    
    # wait until the process is finished and pid was destroyed
    - wait_for: path=/proc/3466/status state=absent
    
    # wait 300 seconds for port 22 to become open and contain "OpenSSH", don't assume the inventory_hostname is resolvable
    # and don't start checking for 10 seconds
    - local_action: wait_for port=22 host="{{ ansible_ssh_host | default(inventory_hostname) }}" search_regex=OpenSSH delay=10
    


Notes
-----

.. note:: The ability to use search_regex with a port connection was added in 1.7.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

