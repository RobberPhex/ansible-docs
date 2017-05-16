.. _mqtt:


mqtt - Publish a message on an MQTT topic for the IoT
+++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Publish a message on an MQTT topic.


Requirements (on host that executes module)
-------------------------------------------

  * mosquitto


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
    <td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>hostname + pid</td>
        <td><ul></ul></td>
        <td><div>MQTT client identifier</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password for <code>username</code> to authenticate against the broker.</div></td></tr>
            <tr>
    <td>payload<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Payload. The special string <code>"None"</code> may be used to send a NULL (i.e. empty) payload which is useful to simply notify with the <em>topic</em> or to clear previously retained messages.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1883</td>
        <td><ul></ul></td>
        <td><div>MQTT broker port number</div></td></tr>
            <tr>
    <td>qos<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>0</li><li>1</li><li>2</li></ul></td>
        <td><div>QoS (Quality of Service)</div></td></tr>
            <tr>
    <td>retain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Setting this flag causes the broker to retain (i.e. keep) the message so that applications that subsequently subscribe to the topic can received the last retained message immediately.</div></td></tr>
            <tr>
    <td>server<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>MQTT broker address/name</div></td></tr>
            <tr>
    <td>topic<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>MQTT topic name</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username to authenticate against the broker.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - local_action: mqtt
                  topic=service/ansible/{{ ansible_hostname }}
                  payload="Hello at {{ ansible_date_time.iso8601 }}"
                  qos=0
                  retain=false
                  client_id=ans001


Notes
-----

.. note:: This module requires a connection to an MQTT broker such as Mosquitto http://mosquitto.org and the *Paho* ``mqtt`` Python client (https://pypi.python.org/pypi/paho-mqtt).


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

