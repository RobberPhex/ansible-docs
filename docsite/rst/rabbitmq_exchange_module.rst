.. _rabbitmq_exchange:


rabbitmq_exchange - This module manages rabbitMQ exchanges
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module uses rabbitMQ Rest API to create/delete exchanges


Requirements
------------

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
    <td>auto_delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if the exchange should delete itself after all queues/exchanges unbound from it</div></td></tr>
            <tr>
    <td>durable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>whether exchange is durable or not</div></td></tr>
            <tr>
    <td>exchange_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>direct</td>
        <td><ul><li>fanout</li><li>direct</li><li>headers</li><li>topic</li></ul></td>
        <td><div>type for the exchange</div></br>
        <div style="font-size: small;">aliases: type<div></td></tr>
            <tr>
    <td>internal<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>exchange is available only for other exchanges</div></td></tr>
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
        <td><div>Name of the exchange to create</div></td></tr>
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
        <td><div>rabbitMQ virtual host</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create direct exchange
    - rabbitmq_exchange: name=directExchange
    
    # Create topic exchange on vhost
    - rabbitmq_exchange: name=topicExchange type=topic vhost=myVhost




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

