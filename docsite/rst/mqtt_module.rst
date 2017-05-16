.. _mqtt:


mqtt - Publish a message on an MQTT topic for the IoT
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Publish a message on an MQTT topic.

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
    <td>client_id</td>
    <td>no</td>
    <td>hostname + pid</td>
        <td><ul></ul></td>
        <td>MQTT client identifier</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Password for <code>username</code> to authenticate against the broker.</td>
    </tr>
            <tr>
    <td>payload</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Payload. The special string <code>"None"</code> may be used to send a NULL (i.e. empty) payload which is useful to simply notify with the <em>topic</em> or to clear previously retained messages.</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>1883</td>
        <td><ul></ul></td>
        <td>MQTT broker port number</td>
    </tr>
            <tr>
    <td>qos</td>
    <td>no</td>
    <td></td>
        <td><ul><li>0</li><li>1</li><li>2</li></ul></td>
        <td>QoS (Quality of Service)</td>
    </tr>
            <tr>
    <td>retain</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Setting this flag causes the broker to retain (i.e. keep) the message so that applications that subsequently subscribe to the topic can received the last retained message immediately.</td>
    </tr>
            <tr>
    <td>server</td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td>MQTT broker address/name</td>
    </tr>
            <tr>
    <td>topic</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>MQTT topic name</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Username to authenticate against the broker.</td>
    </tr>
        </table>


.. note:: Requires mosquitto


Examples
--------

.. raw:: html

    <br/>


::

    - local_action: mqtt
                  topic=service/ansible/{{ ansible_hostname }}
                  payload="Hello at {{ ansible_date_time.iso8601 }}"
                  qos=0
                  retain=false
                  client_id=ans001

.. note:: This module requires a connection to an MQTT broker such as Mosquitto http://mosquitto.org and the *Paho* ``mqtt`` Python client (https://pypi.python.org/pypi/paho-mqtt).


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

