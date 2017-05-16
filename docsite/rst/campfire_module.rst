.. _campfire:


campfire - Send a message to Campfire
+++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Send a message to Campfire.
Messages with newlines will result in a "Paste" message being sent.




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
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The message body.</div></td></tr>
            <tr>
    <td>notify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>56k</li><li>bell</li><li>bezos</li><li>bueller</li><li>clowntown</li><li>cottoneyejoe</li><li>crickets</li><li>dadgummit</li><li>dangerzone</li><li>danielsan</li><li>deeper</li><li>drama</li><li>greatjob</li><li>greyjoy</li><li>guarantee</li><li>heygirl</li><li>horn</li><li>horror</li><li>inconceivable</li><li>live</li><li>loggins</li><li>makeitso</li><li>noooo</li><li>nyan</li><li>ohmy</li><li>ohyeah</li><li>pushit</li><li>rimshot</li><li>rollout</li><li>rumble</li><li>sax</li><li>secret</li><li>sexyback</li><li>story</li><li>tada</li><li>tmyk</li><li>trololo</li><li>trombone</li><li>unix</li><li>vuvuzela</li><li>what</li><li>whoomp</li><li>yeah</li><li>yodel</li></ul></td>
        <td><div>Send a notification sound before the message.</div></td></tr>
            <tr>
    <td>room<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Room number to which the message should be sent.</div></td></tr>
            <tr>
    <td>subscription<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The subscription name to use.</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API token.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - campfire: subscription=foo token=12345 room=123 msg="Task completed."
    
    - campfire: subscription=foo token=12345 room=123 notify=loggins
            msg="Task completed ... with feeling."




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

