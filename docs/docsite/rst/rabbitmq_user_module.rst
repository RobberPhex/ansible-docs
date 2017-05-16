.. _rabbitmq_user:


rabbitmq_user - Adds or removes users to RabbitMQ
+++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove users to RabbitMQ and assign permissions




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
                <tr><td>configure_priv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>^$</td>
        <td></td>
        <td><div>Regular expression to restrict configure actions on a resource for the specified vhost.</div><div>By default all actions are restricted.</div><div>This option will be ignored when permissions option is used.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Deletes and recreates the user.</div>        </td></tr>
                <tr><td>node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>rabbit</td>
        <td></td>
        <td><div>erlang node name of the rabbit we wish to configure</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of user to add.</div><div>To change the password of an existing user, you must also specify <code>force=yes</code>.</div>        </td></tr>
                <tr><td>permissions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a list of dicts, each dict contains vhost, configure_priv, write_priv, and read_priv, and represents a permission rule for that vhost.</div><div>This option should be preferable when you care about all permissions of the user.</div><div>You should use vhost, configure_priv, write_priv, and read_priv options instead if you care about permissions for just some vhosts.</div>        </td></tr>
                <tr><td>read_priv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>^$</td>
        <td></td>
        <td><div>Regular expression to restrict configure actions on a resource for the specified vhost.</div><div>By default all actions are restricted.</div><div>This option will be ignored when permissions option is used.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specify if user is to be added or removed</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User tags specified as comma delimited</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of user to add</div></br>
    <div style="font-size: small;">aliases: username, name<div>        </td></tr>
                <tr><td>vhost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td></td>
        <td><div>vhost to apply access privileges.</div><div>This option will be ignored when permissions option is used.</div>        </td></tr>
                <tr><td>write_priv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>^$</td>
        <td></td>
        <td><div>Regular expression to restrict configure actions on a resource for the specified vhost.</div><div>By default all actions are restricted.</div><div>This option will be ignored when permissions option is used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add user to server and assign full access control on / vhost.
    # The user might have permission rules for other vhost but you don't care.
    - rabbitmq_user:
        user: joe
        password: changeme
        vhost: /
        configure_priv: .*
        read_priv: .*
        write_priv: .*
        state: present
    
    # Add user to server and assign full access control on / vhost.
    # The user doesn't have permission rules for other vhosts
    - rabbitmq_user:
        user: joe
        password: changeme
        permissions:
          - vhost: /
            configure_priv: .*
            read_priv: .*
            write_priv: .*
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
