.. _rabbitmq_parameter:


rabbitmq_parameter - Adds or removes parameters to RabbitMQ
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage dynamic, cluster-wide parameters for RabbitMQ




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
    <td>component<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the component of which the parameter is being set</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the parameter being set</div></td></tr>
            <tr>
    <td>node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>rabbit</td>
        <td><ul></ul></td>
        <td><div>erlang node name of the rabbit we wish to configure</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specify if user is to be added or removed</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Value of the parameter, as a JSON term</div></td></tr>
            <tr>
    <td>vhost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td><ul></ul></td>
        <td><div>vhost to apply access privileges.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set the federation parameter 'local_username' to a value of 'guest' (in quotes)
    - rabbitmq_parameter: component=federation
                          name=local-username
                          value='"guest"'
                          state=present




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

