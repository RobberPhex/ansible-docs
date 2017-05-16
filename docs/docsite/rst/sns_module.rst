.. _sns:


sns - Send Amazon Simple Notification Service (SNS) messages
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``sns`` module sends notifications to a topic on your Amazon SNS account


Requirements (on host that executes module)
-------------------------------------------

  * boto


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
                <tr><td>aws_access_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_access_key, access_key<div>        </td></tr>
                <tr><td>aws_secret_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_secret_key, secret_key<div>        </td></tr>
                <tr><td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Message to send to email-only subscription</div>        </td></tr>
                <tr><td>http<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Message to send to HTTP-only subscription</div>        </td></tr>
                <tr><td>https<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Message to send to HTTPS-only subscription</div>        </td></tr>
                <tr><td>message_attributes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Dictionary of message attributes. These are optional structured data entries to be sent along to the endpoint.</div><div>This is in AWS's distinct Name/Type/Value format; see example below.</div>        </td></tr>
                <tr><td>message_structure<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>json</td>
        <td><ul><li>json</li><li>string</li></ul></td>
        <td><div>The payload format to use for the message.</div><div>This must be 'json' to support non-default messages (`http`, `https`, `email`, `sms`, `sqs`). It must be 'string' to support message_attributes.</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Default message to send.</div></br>
    <div style="font-size: small;">aliases: default<div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>sms<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Message to send to SMS-only subscription</div>        </td></tr>
                <tr><td>sqs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Message to send to SQS-only subscription</div>        </td></tr>
                <tr><td>subject<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Subject line for email delivery.</div>        </td></tr>
                <tr><td>topic<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The topic you want to publish to.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Send default notification message via SNS
      sns:
        msg: '{{ inventory_hostname }} has completed the play.'
        subject: Deploy complete!
        topic: deploy
      delegate_to: localhost
    
    - name: Send notification messages via SNS with short message for SMS
      sns:
        msg: '{{ inventory_hostname }} has completed the play.'
        sms: deployed!
        subject: Deploy complete!
        topic: deploy
      delegate_to: localhost
    
    - name: Send message with message_attributes
      sns:
        topic: "deploy"
        msg: "message with extra details!"
        message_attributes:
          channel:
            data_type: String
            string_value: "mychannel"
          color:
            data_type: String
            string_value: "green"
      delegate_to: localhost





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
