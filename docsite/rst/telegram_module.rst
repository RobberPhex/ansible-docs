.. _telegram:


telegram - module for sending notifications via telegram
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Send notifications via telegram bot, to a verified group or user




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
    <td>chat_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Telegram group or user chat_id</div></td></tr>
            <tr>
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>What message you wish to send.</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Token identifying your telegram bot.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    send a message to chat in playbook
    - telegram:  token=bot9999999:XXXXXXXXXXXXXXXXXXXXXXX
        chat_id=000000
        msg="Ansible task finished"
    

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> msg </td>
        <td> The message you attempted to send </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Ansible task finished </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: You will require a telegram account and create telegram bot to use this module.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

