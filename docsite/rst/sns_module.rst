.. _sns:


sns - Send Amazon Simple Notification Service (SNS) messages
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`sns <sns>` module sends notifications to a topic on your Amazon SNS account


Requirements
------------

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
            <tr>
    <td>aws_access_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used.</div></br>
        <div style="font-size: small;">aliases: ec2_access_key, access_key<div></td></tr>
            <tr>
    <td>aws_secret_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used.</div></br>
        <div style="font-size: small;">aliases: ec2_secret_key, secret_key<div></td></tr>
            <tr>
    <td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Message to send to email-only subscription</div></td></tr>
            <tr>
    <td>http<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Message to send to HTTP-only subscription</div></td></tr>
            <tr>
    <td>https<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Message to send to HTTPS-only subscription</div></td></tr>
            <tr>
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Default message to send.</div></br>
        <div style="font-size: small;">aliases: default<div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>sms<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Message to send to SMS-only subscription</div></td></tr>
            <tr>
    <td>sqs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Message to send to SQS-only subscription</div></td></tr>
            <tr>
    <td>subject<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Subject line for email delivery.</div></td></tr>
            <tr>
    <td>topic<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The topic you want to publish to.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Send default notification message via SNS
      local_action:
        module: sns
        msg: "{{ inventory_hostname }} has completed the play."
        subject: "Deploy complete!"
        topic: "deploy"
    
    - name: Send notification messages via SNS with short message for SMS
      local_action:
        module: sns
        msg: "{{ inventory_hostname }} has completed the play."
        sms: "deployed!"
        subject: "Deploy complete!"
        topic: "deploy"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

