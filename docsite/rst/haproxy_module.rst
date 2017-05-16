.. _haproxy:


haproxy - An Ansible module to handle states enable/disable server and set weight to backend host in haproxy using socket commands.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

The Enable Haproxy Backend Server, with supports get current weight for server (default) and set weight for haproxy backend server when provides.
The Disable Haproxy Backend Server, with supports get current weight for server (default) and shutdown sessions while disabling backend host server.

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
    <td>backend</td>
    <td>no</td>
    <td>auto-detected</td>
        <td><ul></ul></td>
        <td>Name of the haproxy backend pool. Required, else auto-detection applied.</td>
    </tr>
            <tr>
    <td>host</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Host (backend) to operate in Haproxy.</td>
    </tr>
            <tr>
    <td>shutdown_sessions</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>When disabling server, immediately terminate all the sessions attached to the specified server. This can be used to terminate long-running sessions after a server is put into maintenance mode, for instance.</td>
    </tr>
            <tr>
    <td>socket</td>
    <td>no</td>
    <td>/var/run/haproxy.sock</td>
        <td><ul></ul></td>
        <td>Haproxy socket file name with path.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td>describe the desired state of the given host in lb pool.</td>
    </tr>
            <tr>
    <td>weight</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The value passed in argument. If the value ends with the '%' sign, then the new weight will be relative to the initially cnfigured weight. Relative weights are only permitted between 0 and 100% and absolute weights are permitted between 0 and 256.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    examples:
    
    # disable server in 'www' backend pool
    - haproxy: state=disabled host={{ inventory_hostname }} backend=www
    
    # disable server without backend pool name (apply to all available backend pool)
    - haproxy: state=disabled host={{ inventory_hostname }}
    
    # disable server, provide socket file
    - haproxy: state=disabled host={{ inventory_hostname }} socket=/var/run/haproxy.sock backend=www
    
    # disable backend server in 'www' backend pool and drop open sessions to it
    - haproxy: state=disabled host={{ inventory_hostname }} backend=www socket=/var/run/haproxy.sock shutdown_sessions=true
    
    # enable server in 'www' backend pool
    - haproxy: state=enabled host={{ inventory_hostname }} backend=www
    
    # enable server in 'www' backend pool with change server(s) weight
    - haproxy: state=enabled host={{ inventory_hostname }} socket=/var/run/haproxy.sock weight=10 backend=www
    
    author: Ravi Bhure <ravibhure@gmail.com>

.. note:: enable or disable commands are restricted and can only be issued on sockets configured for level 'admin', 
.. note:: Check - http://haproxy.1wt.eu/download/1.5/doc/configuration.txt, 
.. note:: Example: 'stats socket /var/run/haproxy.sock level admin'


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

