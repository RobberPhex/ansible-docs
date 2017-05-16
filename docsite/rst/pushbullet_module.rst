.. _pushbullet:


pushbullet - Sends notifications to Pushbullet
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module sends push notifications via Pushbullet to channels or devices.


Requirements (on host that executes module)
-------------------------------------------

  * pushbullet.py


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
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Push bullet API token</div></td></tr>
            <tr>
    <td>body<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Body of the notification, e.g. Details of the fault you're alerting.</div></td></tr>
            <tr>
    <td>channel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The channel TAG you wish to broadcast a push notification, as seen on the "My Channels" &gt; "Edit your channel" at Pushbullet page.</div></td></tr>
            <tr>
    <td>device<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The device NAME you wish to send a push notification, as seen on the Pushbullet main page.</div></td></tr>
            <tr>
    <td>push_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>note</td>
        <td><ul><li>note</li><li>link</li></ul></td>
        <td><div>Thing you wish to push.</div></td></tr>
            <tr>
    <td>title<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Title of the notification.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Sends a push notification to a device
    - pushbullet: 
        api_key: "ABC123abc123ABC123abc123ABC123ab"
        device: "Chrome"
        title: "You may see this on Google Chrome"
    
    # Sends a link to a device
    - pushbullet: 
        api_key: "ABC123abc123ABC123abc123ABC123ab"
        device: "Chrome"
        push_type: "link"
        title: "Ansible Documentation"
        body: "http://docs.ansible.com/"
    
    # Sends a push notification to a channel
    - pushbullet: 
        api_key: "ABC123abc123ABC123abc123ABC123ab"
        channel: "my-awesome-channel"
        title: "Broadcasting a message to the #my-awesome-channel folks"
    
    # Sends a push notification with title and body to a channel
    - pushbullet: 
        api_key: "ABC123abc123ABC123abc123ABC123ab"
        channel: "my-awesome-channel"
        title: "ALERT! Signup service is down"
        body: "Error rate on signup service is over 90% for more than 2 minutes"


Notes
-----

.. note:: Requires pushbullet.py Python package on the remote host. You can install it via pip with ($ pip install pushbullet.py). See https://github.com/randomchars/pushbullet.py


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

