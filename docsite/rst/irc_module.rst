.. _irc:


irc - Send a message to an IRC channel
++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Send a message to an IRC channel. This is a very simplistic implementation.


Requirements (on host that executes module)
-------------------------------------------

  * socket


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
    <td>channel<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Channel name.  One of nick_to or channel needs to be set.  When both are set, the message will be sent to both of them.</div></td></tr>
            <tr>
    <td>color<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul><li>none</li><li>white</li><li>black</li><li>blue</li><li>green</li><li>red</li><li>brown</li><li>purple</li><li>orange</li><li>yellow</li><li>light_green</li><li>teal</li><li>light_cyan</li><li>light_blue</li><li>pink</li><li>gray</li><li>light_gray</li></ul></td>
        <td><div>Text color for the message. ("none" is a valid option in 1.6 or later, in 1.6 and prior, the default color is black, not "none"). Added 11 more colors in version 2.0.</div></td></tr>
            <tr>
    <td>key<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Channel key</div></td></tr>
            <tr>
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The message body.</div></td></tr>
            <tr>
    <td>nick<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ansible</td>
        <td><ul></ul></td>
        <td><div>Nickname to send the message from. May be shortened, depending on server's NICKLEN setting.</div></td></tr>
            <tr>
    <td>nick_to<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of nicknames to send the message to. One of nick_to or channel needs to be set.  When both are defined, the message will be sent to both of them.</div></td></tr>
            <tr>
    <td>part<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Designates whether user should part from channel after sending message or not. Useful for when using a faux bot and not wanting join/parts between messages.</div></td></tr>
            <tr>
    <td>passwd<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Server password</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>6667</td>
        <td><ul></ul></td>
        <td><div>IRC server port number</div></td></tr>
            <tr>
    <td>server<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>IRC server name/address</div></td></tr>
            <tr>
    <td>style<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>bold</li><li>underline</li><li>reverse</li><li>italic</li></ul></td>
        <td><div>Text style for the message. Note italic does not work on some clients</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>Timeout to use while waiting for successful registration and join messages, this is to prevent an endless loop</div></td></tr>
            <tr>
    <td>topic<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set the channel topic</div></td></tr>
            <tr>
    <td>use_ssl<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Designates whether TLS/SSL should be used when connecting to the IRC server</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - irc: server=irc.example.net channel="#t1" msg="Hello world"
    
    - local_action: irc port=6669
                    server="irc.example.net"
                    channel="#t1"
                    msg="All finished at {{ ansible_date_time.iso8601 }}"
                    color=red
                    nick=ansibleIRC
    
    - local_action: irc port=6669
                    server="irc.example.net"
                    channel="#t1"
                    nick_to=["nick1", "nick2"]
                    msg="All finished at {{ ansible_date_time.iso8601 }}"
                    color=red
                    nick=ansibleIRC




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

