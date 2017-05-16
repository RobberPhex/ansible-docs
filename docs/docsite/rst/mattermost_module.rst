.. _mattermost:


mattermost - Send Mattermost notifications
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Sends notifications to http://your.mattermost.url via the Incoming WebHook integration.




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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Mattermost webhook api key. Log into your mattermost site, go to Menu -&gt; Integration -&gt; Incomming Webhook -&gt; Add Incomming Webhook. This will give you full URL. api_key is the last part. http://mattermost.example.com/hooks/<code>API_KEY</code></div>        </td></tr>
                <tr><td>channel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Channel to send the message to. If absent, the message goes to the channel selected for the <em>api_key</em>.</div>        </td></tr>
                <tr><td>icon_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://www.ansible.com/favicon.ico</td>
        <td></td>
        <td><div>Url for the message sender's icon.</div>        </td></tr>
                <tr><td>text<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Text to send. Note that the module does not handle escaping characters.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Mattermost url (i.e. http://mattermost.yourcompany.com).</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Ansible</td>
        <td></td>
        <td><div>This is the sender of the message (Username Override need to be enabled by mattermost admin, see mattermost doc.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Send notification message via Mattermost
      mattermost:
        url: http://mattermost.example.com
        api_key: my_api_key
        text: '{{ inventory_hostname }} completed'
    
    - name: Send notification message via Mattermost all options
      mattermost:
        url: http://mattermost.example.com
        api_key: my_api_key
        text: '{{ inventory_hostname }} completed'
        channel: notifications
        username: 'Ansible on {{ inventory_hostname }}'
        icon_url: http://www.example.com/some-image-file.png

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
        <td> webhook_url </td>
        <td> URL the webhook is sent to </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> payload </td>
        <td> Mattermost payload </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
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
