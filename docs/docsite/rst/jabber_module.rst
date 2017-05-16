.. _jabber:


jabber - Send a message to jabber user or chat room
+++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Send a message to jabber


Requirements (on host that executes module)
-------------------------------------------

  * python xmpp (xmpppy)


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
                <tr><td>encoding<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>message encoding</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>host to connect, overrides user info</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The message body.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>password for user to connect</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5222</td>
        <td></td>
        <td><div>port to connect to, overrides default</div>        </td></tr>
                <tr><td>to<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>user ID or name of the room, when using room use a slash to indicate your nick.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>User as which to connect</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # send a message to a user
    - jabber:
        user: mybot@example.net
        password: secret
        to: friend@example.net
        msg: Ansible task finished
    
    # send a message to a room
    - jabber:
        user: mybot@example.net
        password: secret
        to: mychaps@conference.example.net/ansiblebot
        msg: Ansible task finished
    
    # send a message, specifying the host and port
    - jabber:
        user: mybot@example.net
        host: talk.example.net
        port: 5223
        password: secret
        to: mychaps@example.net
        msg: Ansible task finished





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
