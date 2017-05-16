.. _redhat_subscription:


redhat_subscription - Manage Red Hat Network registration and subscriptions using the ``subscription-manager`` command
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Manage registration and subscription to the Red Hat Network entitlement platform.

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
    <td>activationkey</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>supply an activation key for use with registration</td>
    </tr>
            <tr>
    <td>autosubscribe</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Upon successful registration, auto-consume available subscriptions</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Red Hat Network password</td>
    </tr>
            <tr>
    <td>pool</td>
    <td>no</td>
    <td>^$</td>
        <td><ul></ul></td>
        <td>Specify a subscription pool name to consume.  Regular expressions accepted.</td>
    </tr>
            <tr>
    <td>rhsm_baseurl</td>
    <td>no</td>
    <td>Current value from C(/etc/rhsm/rhsm.conf) is the default</td>
        <td><ul></ul></td>
        <td>Specify CDN baseurl</td>
    </tr>
            <tr>
    <td>server_hostname</td>
    <td>no</td>
    <td>Current value from C(/etc/rhsm/rhsm.conf) is the default</td>
        <td><ul></ul></td>
        <td>Specify an alternative Red Hat Network server</td>
    </tr>
            <tr>
    <td>server_insecure</td>
    <td>no</td>
    <td>Current value from C(/etc/rhsm/rhsm.conf) is the default</td>
        <td><ul></ul></td>
        <td>Allow traffic over insecure http</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>whether to register and subscribe (<code>present</code>), or unregister (<code>absent</code>) a system</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Red Hat Network username</td>
    </tr>
        </table>


.. note:: Requires subscription-manager


Examples
--------

.. raw:: html

    <br/>


::

    # Register as user (joe_user) with password (somepass) and auto-subscribe to available content.
    - redhat_subscription: state=present username=joe_user password=somepass autosubscribe=true
    
    # Register with activationkey (1-222333444) and consume subscriptions matching
    # the names (Red hat Enterprise Server) and (Red Hat Virtualization)
    - redhat_subscription: state=present
                           activationkey=1-222333444
                           pool='^(Red Hat Enterprise Server|Red Hat Virtualization)$'

.. note:: In order to register a system, subscription-manager requires either a username and password, or an activationkey.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

