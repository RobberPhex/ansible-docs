.. _mqtt:


mqtt - Publish a message on an MQTT topic for the IoT
+++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Publish a message on an MQTT topic.


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
                <tr><td>ca_certs<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The path to the Certificate Authority certificate files that are to be treated as trusted by this client. If this is the only option given then the client will operate in a similar manner to a web browser. That is to say it will require the broker to have a certificate signed by the Certificate Authorities in ca_certs and will communicate using TLS v1, but will not attempt any form of authentication. This provides basic network encryption but may not be sufficient depending on how the broker is configured.</div>        </td></tr>
                <tr><td>certfile<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The path pointing to the PEM encoded client certificate. If this is not None it will be used as client information for TLS based authentication. Support for this feature is broker dependent.</div>        </td></tr>
                <tr><td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>hostname + pid</td>
        <td></td>
        <td><div>MQTT client identifier</div>        </td></tr>
                <tr><td>keyfile<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The path pointing to the PEM encoded client private key. If this is not None it will be used as client information for TLS based authentication. Support for this feature is broker dependent.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password for <code>username</code> to authenticate against the broker.</div>        </td></tr>
                <tr><td>payload<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Payload. The special string <code>"None"</code> may be used to send a NULL (i.e. empty) payload which is useful to simply notify with the <em>topic</em> or to clear previously retained messages.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1883</td>
        <td></td>
        <td><div>MQTT broker port number</div>        </td></tr>
                <tr><td>qos<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>0</li><li>1</li><li>2</li></ul></td>
        <td><div>QoS (Quality of Service)</div>        </td></tr>
                <tr><td>retain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Setting this flag causes the broker to retain (i.e. keep) the message so that applications that subsequently subscribe to the topic can received the last retained message immediately.</div>        </td></tr>
                <tr><td>server<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>MQTT broker address/name</div>        </td></tr>
                <tr><td>topic<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>MQTT topic name</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username to authenticate against the broker.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - mqtt:
        topic: 'service/ansible/{{ ansible_hostname }}'
        payload: 'Hello at {{ ansible_date_time.iso8601 }}'
        qos: 0
        retain: False
        client_id: ans001
      delegate_to: localhost


Notes
-----

.. note::
    - This module requires a connection to an MQTT broker such as Mosquitto http://mosquitto.org and the *Paho* ``mqtt`` Python client (https://pypi.python.org/pypi/paho-mqtt).



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
