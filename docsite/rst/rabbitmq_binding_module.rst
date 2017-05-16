.. _rabbitmq_binding:


rabbitmq_binding - This module manages rabbitMQ bindings
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module uses rabbitMQ Rest API to create/delete bindings


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
        <td><div>extra arguments for exchange. If defined this argument is a key/value dictionary</div></td></tr>
            <tr>
    <td>destination<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>destination exchange or queue for the binding</div></br>
        <div style="font-size: small;">aliases: dst, dest<div></td></tr>
            <tr>
    <td>destination_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>queue</li><li>exchange</li></ul></td>
        <td><div>Either queue or exchange</div></br>
        <div style="font-size: small;">aliases: type, dest_type<div></td></tr>
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
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>source exchange to create binding on</div></br>
        <div style="font-size: small;">aliases: src, source<div></td></tr>
            <tr>
    <td>routing_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>#</td>
        <td><ul></ul></td>
        <td><div>routing key for the binding</div><div>default is</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the exchange should be present or absent</div><div>Only present implemented atm</div></td></tr>
            <tr>
    <td>vhost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td><ul></ul></td>
        <td><div>rabbitMQ virtual host</div><div>default vhost is /</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Bind myQueue to directExchange with routing key info
    - rabbitmq_binding: name=directExchange destination=myQueue type=queue routing_key=info
    
    # Bind directExchange to topicExchange with routing key *.info
    - rabbitmq_binding: name=topicExchange destination=topicExchange type=exchange routing_key="*.info"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

