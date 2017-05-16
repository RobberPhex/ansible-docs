.. _a10_server_axapi3:


a10_server_axapi3 - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage SLB (Server Load Balancer) server objects on A10 Networks devices via aXAPIv3.




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
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Hostname or IP of the A10 Networks device.</div>        </td></tr>
                <tr><td>operation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>create</td>
        <td><ul><li>create</li><li>update</li><li>remove</li></ul></td>
        <td><div>Create, Update or Remove SLB server. For create and update operation, we use the IP address and server name specified in the POST message. For delete operation, we use the server name in the request URI.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the <code>username</code> account.</div></br>
    <div style="font-size: small;">aliases: pass, pwd<div>        </td></tr>
                <tr><td>server_ip<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The SLB (Server Load Balancer) server IPv4 address.</div></br>
    <div style="font-size: small;">aliases: ip, address<div>        </td></tr>
                <tr><td>server_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The SLB (Server Load Balancer) server name.</div></br>
    <div style="font-size: small;">aliases: server<div>        </td></tr>
                <tr><td>server_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of ports to create for the server. Each list item should be a dictionary which specifies the <code>port:</code> and <code>protocol:</code>.</div>        </td></tr>
                <tr><td>server_status<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>enable</td>
        <td><ul><li>enable</li><li>disable</li></ul></td>
        <td><div>The SLB (Server Load Balancer) virtual server status.</div></br>
    <div style="font-size: small;">aliases: action<div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An account with administrator privileges.</div></br>
    <div style="font-size: small;">aliases: user, admin<div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled devices using self-signed certificates.</div>        </td></tr>
                <tr><td>write_config<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, any changes will cause a write of the running configuration to non-volatile memory. This will save <em>all</em> configuration changes, including those that may have been made manually or through other modules, so care should be taken when specifying <code>yes</code>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new server
    - a10_server:
        host: a10.mydomain.com
        username: myadmin
        password: mypassword
        server: test
        server_ip: 1.1.1.100
        validate_certs: false
        server_status: enable
        write_config: yes
        operation: create
        server_ports:
          - port-number: 8080
            protocol: tcp
            action: enable
          - port-number: 8443
            protocol: TCP
    


Notes
-----

.. note::
    - Requires A10 Networks aXAPI 2.1



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
