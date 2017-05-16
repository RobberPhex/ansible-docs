.. _hipchat:


hipchat - Send a message to Hipchat.
++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Send a message to a Hipchat room, with options to control the formatting.




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
                <tr><td>api<br/><div style="font-size: small;"> (added in 1.6.0)</div></td>
    <td>no</td>
    <td>https://api.hipchat.com/v1</td>
        <td></td>
        <td><div>API url if using a self-hosted hipchat server. For Hipchat API version 2 use the default URI with <code>/v2</code> instead of <code>/v1</code>.</div>        </td></tr>
                <tr><td>color<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yellow</td>
        <td><ul><li>yellow</li><li>red</li><li>green</li><li>purple</li><li>gray</li><li>random</li></ul></td>
        <td><div>Background color for the message.</div>        </td></tr>
                <tr><td>from<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Ansible</td>
        <td></td>
        <td><div>Name the message will appear to be sent from. Max length is 15 characters - above this it will be truncated.</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The message body.</div>        </td></tr>
                <tr><td>msg_format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>text</td>
        <td><ul><li>text</li><li>html</li></ul></td>
        <td><div>Message format.</div>        </td></tr>
                <tr><td>notify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If true, a notification will be triggered for users in the room.</div>        </td></tr>
                <tr><td>room<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>ID or name of the room.</div>        </td></tr>
                <tr><td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>API token.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - hipchat:
        room: notif
        msg: Ansible task finished
    
    # Use Hipchat API version 2
    - hipchat:
        api: https://api.hipchat.com/v2/
        token: OAUTH2_TOKEN
        room: notify
        msg: Ansible task finished





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
