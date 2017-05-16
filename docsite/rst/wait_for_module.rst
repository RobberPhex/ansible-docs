.. _wait_for:


wait_for - Waits for a condition before continuing.
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Waiting for a port to become available is useful for when services are not immediately available after their init scripts return - which is true of certain Java application servers. It is also useful when starting guests with the ``virt`` module and needing to pause until they are ready.
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
    <td>delay</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>number of seconds to wait before starting to poll</td>
    </tr>
            <tr>
    <td>exclude_hosts</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>list of hosts or IPs to ignore when looking for active TCP connections for <code>drained</code> state (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>host</td>
    <td>no</td>
    <td>127.0.0.1</td>
        <td><ul></ul></td>
        <td>hostname or IP address to wait for</td>
    </tr>
            <tr>
    <td>path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to a file on the filesytem that must exist before continuing (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>port number to poll</td>
    </tr>
            <tr>
    <td>search_regex</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Can be used to match a string in either a file or a socket connection. Defaults to a multiline regex. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>present</li><li>started</li><li>stopped</li><li>absent</li><li>drained</li></ul></td>
        <td>either <code>present</code>, <code>started</code>, or <code>stopped</code>, <code>absent</code>, or <code>drained</code>When checking a port <code>started</code> will ensure the port is open, <code>stopped</code> will check that it is closed, <code>drained</code> will check for active connectionsWhen checking for a file or a search string <code>present</code> or <code>started</code> will ensure that the file or string is present before continuing, <code>absent</code> will check that file is absent or removed</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>maximum number of seconds to wait for</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


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
    
    # Wait 300 seconds for port 22 to become open and contain "OpenSSH", don't start checking for 10 seconds
    - local_action: wait_for port=22 host="{{ inventory_hostname }}" search_regex=OpenSSH delay=10
    

.. note:: The ability to use search_regex with a port connection was added in 1.7.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

