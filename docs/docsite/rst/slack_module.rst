.. _slack:


slack - Send Slack notifications
++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``slack`` module sends notifications to http://slack.com via the Incoming WebHook integration




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
        <td><div>Define a list of attachments. This list mirrors the Slack JSON API. For more information, see https://api.slack.com/docs/attachments</div>        </td></tr>
                <tr><td>channel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Channel to send the message to. If absent, the message goes to the channel selected for the <em>token</em>.</div>        </td></tr>
                <tr><td>color<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>normal</td>
        <td><ul><li>normal</li><li>good</li><li>warning</li><li>danger</li></ul></td>
        <td><div>Allow text to use default colors - use the default of 'normal' to not send a custom color bar at the start of the message</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Slack (sub)domain for your environment without protocol. (i.e. <code>example.slack.com</code>) In 1.8 and beyond, this is deprecated and may be ignored.  See token documentation for information.</div>        </td></tr>
                <tr><td>icon_emoji<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Emoji for the message sender. See Slack documentation for options. (if <em>icon_emoji</em> is set, <em>icon_url</em> will not be used)</div>        </td></tr>
                <tr><td>icon_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url for the message sender's icon (default <code>https://www.ansible.com/favicon.ico</code>)</div>        </td></tr>
                <tr><td>link_names<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>1</li><li>0</li></ul></td>
        <td><div>Automatically create links for channels and usernames in <em>msg</em>.</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Message to send. Note that the module does not handle escaping characters. Plain-text angle brackets and ampersands should be converted to HTML entities (e.g. &amp; to &amp;amp;) before sending. See Slack's documentation (<a href='https://api.slack.com/docs/message-formatting'>https://api.slack.com/docs/message-formatting</a>) for more.</div>        </td></tr>
                <tr><td>parse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>full</li><li>none</li></ul></td>
        <td><div>Setting for the message parser at Slack</div>        </td></tr>
                <tr><td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Slack integration token.  This authenticates you to the slack service. Prior to 1.8, a token looked like <code>3Ffe373sfhRE6y42Fg3rvf4GlK</code>.  In 1.8 and above, ansible adapts to the new slack API where tokens look like <code>G922VJP24/D921DW937/3Ffe373sfhRE6y42Fg3rvf4GlK</code>.  If tokens are in the new format then slack will ignore any value of domain.  If the token is in the old format the domain is required.  Ansible has no control of when slack will get rid of the old API.  When slack does that the old format will stop working.  ** Please keep in mind the tokens are not the API tokens but are the webhook tokens.  In slack these are found in the webhook URL which are obtained under the apps and integrations. The incoming webhooks can be added in that area.  In some cases this may be locked by your Slack admin and you must request access.  It is there that the incoming webhooks can be added.  The key is on the end of the URL given to you in that section.</div>        </td></tr>
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

    - name: Send notification message via Slack
      slack:
        token: thetoken/generatedby/slack
        msg: '{{ inventory_hostname }} completed'
      delegate_to: localhost
    
    - name: Send notification message via Slack all options
      slack:
        token: thetoken/generatedby/slack
        msg: '{{ inventory_hostname }} completed'
        channel: #ansible
        username: 'Ansible on {{ inventory_hostname }}'
        icon_url: http://www.example.com/some-image-file.png
        link_names: 0
        parse: 'none'
      delegate_to: localhost
    
    - name: insert a color bar in front of the message for visibility purposes and use the default webhook icon and name configured in Slack
      slack:
        token: thetoken/generatedby/slack
        msg: '{{ inventory_hostname }} is alive!'
        color: good
        username: ''
        icon_url: ''
    
    - name: Use the attachments API
      slack:
        token: thetoken/generatedby/slack
        attachments:
          - text: Display my system load on host A and B
            color: #ff00dd
            title: System load
            fields:
              - title: System A
                value: "load average: 0,74, 0,66, 0,63"
                short: True
              - title: System B
                value: 'load average: 5,16, 4,64, 2,43'
                short: True
    
    - name: Send a message with a link using Slack markup
      slack:
        token: thetoken/generatedby/slack
        msg: We sent this message using <https://www.ansible.com|Ansible>!
    
    - name: Send a message with angle brackets and ampersands
      slack:
        token: thetoken/generatedby/slack
        msg: This message has &lt;brackets&gt; &amp; ampersands in plain text.





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
