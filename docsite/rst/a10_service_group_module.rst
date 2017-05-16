.. _a10_service_group:


a10_service_group - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.8

Manage slb service-group objects on A10 Networks devices via aXAPI

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
    <td>servers</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A list of servers to add to the service group. Each list item should be a dictionary which specifies the <code>server:</code> and <code>port:</code>, but can also optionally specify the <code>status:</code>. See the examples below for details.</td>
    </tr>
            <tr>
    <td>service_group</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>slb service-group name</td>
    </tr>
            <tr>
    <td>service_group_method</td>
    <td>no</td>
    <td>round-robin</td>
        <td><ul><li>round-robin</li><li>weighted-rr</li><li>least-connection</li><li>weighted-least-connection</li><li>service-least-connection</li><li>service-weighted-least-connection</li><li>fastest-response</li><li>least-request</li><li>round-robin-strict</li><li>src-ip-only-hash</li><li>src-ip-hash</li></ul></td>
        <td>slb service-group loadbalancing method</td>
    </tr>
            <tr>
    <td>service_group_protocol</td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>udp</li></ul></td>
        <td>slb service-group protocol</td>
    </tr>
            <tr>
    <td>username</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>admin account of your A10 Networks device</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled devices using self-signed certificates.</td>
    </tr>
            <tr>
    <td>write_config</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>yes</code>, any changes will cause a write of the running configuration to non-volatile memory. This will save <em>all</em> configuration changes, including those that may have been made manually or through other modules, so care should be taken when specifying <code>yes</code>.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Create a new service-group
    - a10_service_group: 
        host: a10.mydomain.com
        username: myadmin
        password: mypassword
        service_group: sg-80-tcp
        servers:
          - server: foo1.mydomain.com
            port: 8080
          - server: foo2.mydomain.com
            port: 8080
          - server: foo3.mydomain.com
            port: 8080
          - server: foo4.mydomain.com
            port: 8080
            status: disabled
    

.. note:: Requires A10 Networks aXAPI 2.1
.. note:: When a server doesn't exist and is added to the service-group the server will be created


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

