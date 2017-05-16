.. _hipchat:


hipchat - Send a message to hipchat.
++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Send a message to hipchat




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
    <td>api<br/><div style="font-size: small;"> (added in 1.6.0)</div></td>
    <td>no</td>
    <td>https://api.hipchat.com/v1</td>
        <td><ul></ul></td>
        <td><div>API url if using a self-hosted hipchat server. For hipchat api version 2 use <code>/v2</code> path in URI</div></td></tr>
            <tr>
    <td>color<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yellow</td>
        <td><ul><li>yellow</li><li>red</li><li>green</li><li>purple</li><li>gray</li><li>random</li></ul></td>
        <td><div>Background color for the message. Default is yellow.</div></td></tr>
            <tr>
    <td>from<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Ansible</td>
        <td><ul></ul></td>
        <td><div>Name the message will appear be sent from. max 15 characters. Over 15, will be shorten.</div></td></tr>
            <tr>
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The message body.</div></td></tr>
            <tr>
    <td>msg_format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>text</td>
        <td><ul><li>text</li><li>html</li></ul></td>
        <td><div>message format. html or text. Default is text.</div></td></tr>
            <tr>
    <td>notify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>notify or not (change the tab color, play a sound, etc)</div></td></tr>
            <tr>
    <td>room<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>ID or name of the room.</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API token.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - hipchat:  room=notify msg="Ansible task finished"
    
    # Use Hipchat API version 2
    
    - hipchat:
        api: "https://api.hipchat.com/v2/"
        token: OAUTH2_TOKEN
        room: notify
        msg: "Ansible task finished"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

