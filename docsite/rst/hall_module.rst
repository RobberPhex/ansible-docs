.. _hall:


hall - Send notification to Hall
++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`hall <hall>` module connects to the https://hall.com messaging API and allows you to deliver notication messages to rooms.




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
        <td><div>The message you wish to deliver as a notifcation</div></td></tr>
            <tr>
    <td>picture<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The full URL to the image you wish to use for the Icon of the message. Defaults to <a href='http://cdn2.hubspot.net/hub/330046/file-769078210-png/Official_Logos/ansible_logo_black_square_small.png?t=1421076128627'>http://cdn2.hubspot.net/hub/330046/file-769078210-png/Official_Logos/ansible_logo_black_square_small.png?t=1421076128627</a></div></td></tr>
            <tr>
    <td>room_token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Room token provided to you by setting up the Ansible room integation on <a href='https://hall.com'>https://hall.com</a></div></td></tr>
            <tr>
    <td>title<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The title of the message</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Send Hall notifiation
      local_action:
        module: hall
        room_token: <hall room integration token>
        title: Nginx
        msg: Created virtual host file on {{ inventory_hostname }}
    
    - name: Send Hall notification if EC2 servers were created.
      when: ec2.instances|length > 0
      local_action:
        module: hall
        room_token: <hall room integration token>
        title: Server Creation
        msg: "Created EC2 instance {{ item.id }} of type {{ item.instance_type }}.\nInstance can be reached at {{ item.public_ip }} in the {{ item.region }} region."
      with_items: ec2.instances




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

