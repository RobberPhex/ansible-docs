.. _redhat_subscription:


redhat_subscription - Manage registration and subscriptions to RHSM using the ``subscription-manager`` command
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage registration and subscription to the Red Hat Subscription Management entitlement platform using the ``subscription-manager`` command


Requirements (on host that executes module)
-------------------------------------------

  * subscription-manager


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
    <td>autosubscribe<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Upon successful registration, auto-consume available subscriptions</div></td></tr>
            <tr>
    <td>consumer_id<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>References an existing consumer ID to resume using a previous registration for this system. If the  system's identity certificate is lost or corrupted, this option allows it to resume using its previous identity and subscriptions. The default is to not specify a consumer ID so a new ID is created.</div></td></tr>
            <tr>
    <td>consumer_name<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the system to register, defaults to the hostname</div></td></tr>
            <tr>
    <td>consumer_type<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The type of unit to register, defaults to system</div></td></tr>
            <tr>
    <td>environment<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Register with a specific environment in the destination org. Used with Red Hat Satellite 6.x or Katello</div></td></tr>
            <tr>
    <td>force_register<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Register the system even if it is already registered</div></td></tr>
            <tr>
    <td>org_id<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Organization ID to use in conjunction with activationkey</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>access.redhat.com or Sat6 password</div></td></tr>
            <tr>
    <td>pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>^$</td>
        <td><ul></ul></td>
        <td><div>Specify a subscription pool name to consume.  Regular expressions accepted.</div></td></tr>
            <tr>
    <td>rhsm_baseurl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Current value from C(/etc/rhsm/rhsm.conf) is the default</td>
        <td><ul></ul></td>
        <td><div>Specify CDN baseurl</div></td></tr>
            <tr>
    <td>server_hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Current value from C(/etc/rhsm/rhsm.conf) is the default</td>
        <td><ul></ul></td>
        <td><div>Specify an alternative Red Hat Subscription Management or Sat6 server</div></td></tr>
            <tr>
    <td>server_insecure<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Current value from C(/etc/rhsm/rhsm.conf) is the default</td>
        <td><ul></ul></td>
        <td><div>Enable or disable https server certificate verification when connecting to <code>server_hostname</code></div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>whether to register and subscribe (<code>present</code>), or unregister (<code>absent</code>) a system</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>access.redhat.com or Sat6  username</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Register as user (joe_user) with password (somepass) and auto-subscribe to available content.
    - redhat_subscription: state=present username=joe_user password=somepass autosubscribe=true
    
    # Same as above but with pulling existing system data.
    - redhat_subscription: state=present username=joe_user password=somepass
                           consumer_id=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    
    # Register with activationkey (1-222333444) and consume subscriptions matching
    # the names (Red hat Enterprise Server) and (Red Hat Virtualization)
    - redhat_subscription: state=present
                           activationkey=1-222333444
                           pool='^(Red Hat Enterprise Server|Red Hat Virtualization)$'
    
    # Update the consumed subscriptions from the previous example (remove the Red
    # Hat Virtualization subscription)
    - redhat_subscription: state=present
                           activationkey=1-222333444
                           pool='^Red Hat Enterprise Server$'
    
    # Register as user credentials into given environment (against Red Hat
    # Satellite 6.x), and auto-subscribe to available content.
    - redhat_subscription: state=present
                           username=joe_user password=somepass
                           environment=Library
                           autosubscribe=true


Notes
-----

.. note:: In order to register a system, subscription-manager requires either a username and password, or an activationkey.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

