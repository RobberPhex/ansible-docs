.. _rabbitmq_user:


rabbitmq_user - Adds or removes users to RabbitMQ
+++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove users to RabbitMQ and assign permissions




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
    <td>configure_priv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>^$</td>
        <td><ul></ul></td>
        <td><div>Regular expression to restrict configure actions on a resource for the specified vhost.</div><div>By default all actions are restricted.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Deletes and recreates the user.</div></td></tr>
            <tr>
    <td>node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>rabbit</td>
        <td><ul></ul></td>
        <td><div>erlang node name of the rabbit we wish to configure</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password of user to add.</div><div>To change the password of an existing user, you must also specify <code>force=yes</code>.</div></td></tr>
            <tr>
    <td>read_priv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>^$</td>
        <td><ul></ul></td>
        <td><div>Regular expression to restrict configure actions on a resource for the specified vhost.</div><div>By default all actions are restricted.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specify if user is to be added or removed</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>User tags specified as comma delimited</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of user to add</div></br>
        <div style="font-size: small;">aliases: username, name<div></td></tr>
            <tr>
    <td>vhost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td><ul></ul></td>
        <td><div>vhost to apply access privileges.</div></td></tr>
            <tr>
    <td>write_priv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>^$</td>
        <td><ul></ul></td>
        <td><div>Regular expression to restrict configure actions on a resource for the specified vhost.</div><div>By default all actions are restricted.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add user to server and assign full access control
    - rabbitmq_user: user=joe
                     password=changeme
                     vhost=/
                     configure_priv=.*
                     read_priv=.*
                     write_priv=.*
                     state=present




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

