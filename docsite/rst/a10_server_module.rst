.. _a10_server:


a10_server - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.8

Manage slb server objects on A10 Networks devices via aXAPI

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
    <td>host</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>hostname or ip of your A10 Networks device</td>
    </tr>
            <tr>
    <td>password</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>admin password of your A10 Networks device</td>
    </tr>
            <tr>
    <td>server_ip</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>slb server IP address</td>
    </tr>
            <tr>
    <td>server_name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>slb server name</td>
    </tr>
            <tr>
    <td>server_ports</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A list of ports to create for the server. Each list item should be a dictionary which specifies the <code>port:</code> and <code>protocol:</code>, but can also optionally specify the <code>status:</code>. See the examples below for details. This parameter is required when <code>state</code> is <code>present</code>.</td>
    </tr>
            <tr>
    <td>server_status</td>
    <td>no</td>
    <td>enable</td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td>slb virtual server status</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>create, update or remove slb server</td>
    </tr>
            <tr>
    <td>username</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>admin account of your A10 Networks device</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Create a new server
    - a10_server: 
        host: a10.mydomain.com
        username: myadmin
        password: mypassword
        server: test
        server_ip: 1.1.1.100
        server_ports:
          - port_num: 8080
            protocol: tcp
          - port_num: 8443
            protocol: TCP
    

.. note:: Requires A10 Networks aXAPI 2.1


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

