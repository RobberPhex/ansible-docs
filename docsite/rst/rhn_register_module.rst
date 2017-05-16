.. _rhn_register:


rhn_register - Manage Red Hat Network registration using the ``rhnreg_ks`` command
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage registration to the Red Hat Network.


Requirements (on host that executes module)
-------------------------------------------

  * rhnreg_ks


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
    <td>activationkey<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>supply an activation key for use with registration</div></td></tr>
            <tr>
    <td>channels<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally specify a list of comma-separated channels to subscribe to upon successful registration.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Red Hat Network password</div></td></tr>
            <tr>
    <td>profilename<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>supply an profilename for use with registration</div></td></tr>
            <tr>
    <td>server_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Current value of I(serverURL) from C(/etc/sysconfig/rhn/up2date) is the default</td>
        <td><ul></ul></td>
        <td><div>Specify an alternative Red Hat Network server URL</div></td></tr>
            <tr>
    <td>sslcacert<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>supply a custom ssl CA certificate file for use with registration</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>whether to register (<code>present</code>), or unregister (<code>absent</code>) a system</div></td></tr>
            <tr>
    <td>systemorgid<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>supply an organizational id for use with registration</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Red Hat Network username</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Unregister system from RHN.
    - rhn_register: state=absent username=joe_user password=somepass
    
    # Register as user (joe_user) with password (somepass) and auto-subscribe to available content.
    - rhn_register: state=present username=joe_user password=somepass
    
    # Register with activationkey (1-222333444) and enable extended update support.
    - rhn_register: state=present activationkey=1-222333444 enable_eus=true
    
    # Register with activationkey (1-222333444) and set a profilename which may differ from the hostname.
    - rhn_register: state=present activationkey=1-222333444 profilename=host.example.com.custom
    
    # Register as user (joe_user) with password (somepass) against a satellite
    # server specified by (server_url).
    - rhn_register: >
        state=present
        username=joe_user
        password=somepass
        server_url=https://xmlrpc.my.satellite/XMLRPC
    
    # Register as user (joe_user) with password (somepass) and enable
    # channels (rhel-x86_64-server-6-foo-1) and (rhel-x86_64-server-6-bar-1).
    - rhn_register: state=present username=joe_user
                    password=somepass
                    channels=rhel-x86_64-server-6-foo-1,rhel-x86_64-server-6-bar-1


Notes
-----

.. note:: In order to register a system, rhnreg_ks requires either a username and password, or an activationkey.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

