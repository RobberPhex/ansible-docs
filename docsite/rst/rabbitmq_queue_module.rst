.. _rabbitmq_queue:


rabbitmq_queue - This module manages rabbitMQ queues
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module uses rabbitMQ Rest API to create/delete queues


Requirements (on host that executes module)
-------------------------------------------

  * python requests


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
    <td>arguments<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>extra arguments for queue. If defined this argument is a key/value dictionary</div></td></tr>
            <tr>
    <td>auto_delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if the queue should delete itself after all queues/queues unbound from it</div></td></tr>
            <tr>
    <td>auto_expires<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>forever</td>
        <td><ul></ul></td>
        <td><div>How long a queue can be unused before it is automatically deleted (milliseconds)</div></td></tr>
            <tr>
    <td>dead_letter_exchange<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Optional name of an exchange to which messages will be republished if they</div><div>are rejected or expire</div></td></tr>
            <tr>
    <td>dead_letter_routing_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Optional replacement routing key to use when a message is dead-lettered.</div><div>Original routing key will be used if unset</div></td></tr>
            <tr>
    <td>durable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>whether queue is durable or not</div></td></tr>
            <tr>
    <td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>rabbitMQ host for connection</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>rabbitMQ password for connection</div></td></tr>
            <tr>
    <td>login_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>15672</td>
        <td><ul></ul></td>
        <td><div>rabbitMQ management api port</div></td></tr>
            <tr>
    <td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>guest</td>
        <td><ul></ul></td>
        <td><div>rabbitMQ user for connection</div></td></tr>
            <tr>
    <td>max_length<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no limit</td>
        <td><ul></ul></td>
        <td><div>How many messages can the queue contain before it starts rejecting</div></td></tr>
            <tr>
    <td>message_ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>forever</td>
        <td><ul></ul></td>
        <td><div>How long a message can live in queue before it is discarded (milliseconds)</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the queue to create</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the queue should be present or absent</div><div>Only present implemented atm</div></td></tr>
            <tr>
    <td>vhost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td><ul></ul></td>
        <td><div>rabbitMQ virtual host</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a queue
    - rabbitmq_queue: name=myQueue
    
    # Create a queue on remote host
    - rabbitmq_queue: name=myRemoteQueue login_user=user login_password=secret login_host=remote.example.org




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

