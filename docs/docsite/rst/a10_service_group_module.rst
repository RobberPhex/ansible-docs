.. _a10_service_group:


a10_service_group - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices' service groups.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.8


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage SLB (Server Load Balancing) service-group objects on A10 Networks devices via aXAPIv2.




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
                <tr><td>partition<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>set active-partition</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the <code>username</code> account.</div></br>
    <div style="font-size: small;">aliases: pass, pwd<div>        </td></tr>
                <tr><td>servers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of servers to add to the service group. Each list item should be a dictionary which specifies the <code>server:</code> and <code>port:</code>, but can also optionally specify the <code>status:</code>. See the examples below for details.</div>        </td></tr>
                <tr><td>service_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The SLB (Server Load Balancing) service-group name</div></br>
    <div style="font-size: small;">aliases: service, pool, group<div>        </td></tr>
                <tr><td>service_group_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>round-robin</td>
        <td><ul><li>round-robin</li><li>weighted-rr</li><li>least-connection</li><li>weighted-least-connection</li><li>service-least-connection</li><li>service-weighted-least-connection</li><li>fastest-response</li><li>least-request</li><li>round-robin-strict</li><li>src-ip-only-hash</li><li>src-ip-hash</li></ul></td>
        <td><div>The SLB service-group load balancing method, such as round-robin or weighted-rr.</div></br>
    <div style="font-size: small;">aliases: method<div>        </td></tr>
                <tr><td>service_group_protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>udp</li></ul></td>
        <td><div>The SLB service-group protocol of TCP or UDP.</div></br>
    <div style="font-size: small;">aliases: proto, protocol<div>        </td></tr>
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

    # Create a new service-group
    - a10_service_group:
        host: a10.mydomain.com
        username: myadmin
        password: mypassword
        partition: mypartition
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
    

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> content </td>
        <td> the full info regarding the slb_service_group </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> mynewservicegroup </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Requires A10 Networks aXAPI 2.1.
    - When a server doesn't exist and is added to the service-group the server will be created.
    - Requires A10 Networks aXAPI 2.1



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
