.. _typetalk:


typetalk - Send a message to typetalk
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Send a message to typetalk using typetalk API ( http://developers.typetalk.in/ )


Requirements (on host that executes module)
-------------------------------------------

  * json


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
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>OAuth2 client ID</div></td></tr>
            <tr>
    <td>client_secret<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>OAuth2 client secret</div></td></tr>
            <tr>
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>message body</div></td></tr>
            <tr>
    <td>topic<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>topic id to post message</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - typetalk: client_id=12345 client_secret=12345 topic=1 msg="install completed"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

