.. _rocketchat:


rocketchat - Send notifications to Rocket Chat
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``rocketchat`` module sends notifications to Rocket Chat via the Incoming WebHook integration




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
                <tr><td>attachments<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Define a list of attachments.</div>        </td></tr>
                <tr><td>channel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Channel to send the message to. If absent, the message goes to the channel selected for the <em>token</em> specifed during the creation of webhook.</div>        </td></tr>
                <tr><td>color<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>normal</td>
        <td><ul><li>normal</li><li>good</li><li>warning</li><li>danger</li></ul></td>
        <td><div>Allow text to use default colors - use the default of 'normal' to not send a custom color bar at the start of the message</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The domain for your environment without protocol. (i.e. <code>example.com</code> or <code>chat.example.com</code>)</div>        </td></tr>
                <tr><td>icon_emoji<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Emoji for the message sender. The representation for the available emojis can be got from Rocket Chat. (for example :thumbsup:) (if <em>icon_emoji</em> is set, <em>icon_url</em> will not be used)</div>        </td></tr>
                <tr><td>icon_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://www.ansible.com/favicon.ico</td>
        <td></td>
        <td><div>URL for the message sender's icon.</div>        </td></tr>
                <tr><td>link_names<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>1</li><li>0</li></ul></td>
        <td><div>Automatically create links for channels and usernames in <em>msg</em>.</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Message to be sent.</div>        </td></tr>
                <tr><td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https</td>
        <td><ul><li>http</li><li>https</li></ul></td>
        <td><div>Specify the protocol used to send notification messages before the webhook url. (i.e. http or https)</div>        </td></tr>
                <tr><td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Rocket Chat Incoming Webhook integration token.  This provides authentication to Rocket Chat's Incoming webhook for posting messages.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Ansible</td>
        <td></td>
        <td><div>This is the sender of the message.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Send notification message via Rocket Chat
      rocketchat:
        token: thetoken/generatedby/rocketchat
        domain: chat.example.com
        msg: '{{ inventory_hostname }} completed'
      delegate_to: localhost
    
    - name: Send notification message via Rocket Chat all options
      rocketchat:
        domain: chat.example.com
        token: thetoken/generatedby/rocketchat
        msg: '{{ inventory_hostname }} completed'
        channel: #ansible
        username: 'Ansible on {{ inventory_hostname }}'
        icon_url: http://www.example.com/some-image-file.png
        link_names: 0
      delegate_to: localhost
    
    - name: insert a color bar in front of the message for visibility purposes and use the default webhook icon and name configured in rocketchat
      rocketchat:
        token: thetoken/generatedby/rocketchat
        domain: chat.example.com
        msg: '{{ inventory_hostname }} is alive!'
        color: good
        username: ''
        icon_url: ''
      delegate_to: localhost
    
    - name: Use the attachments API
      rocketchat:
        token: thetoken/generatedby/rocketchat
        domain: chat.example.com
        attachments:
          - text: Display my system load on host A and B
            color: #ff00dd
            title: System load
            fields:
              - title: System A
                value: 'load average: 0,74, 0,66, 0,63'
                short: True
              - title: System B
                value: 'load average: 5,16, 4,64, 2,43'
                short: True
      delegate_to: localhost

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
        <td> changed </td>
        <td> A flag indicating if any change was made or not. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
