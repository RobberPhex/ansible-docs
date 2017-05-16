.. _sns:


sns - Send Amazon Simple Notification Service (SNS) messages
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

The ``sns`` module sends notifications to a topic on your Amazon SNS account

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
    <td>aws_access_key</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>aws_secret_key</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>email</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Message to send to email-only subscription</td>
    </tr>
            <tr>
    <td>http</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Message to send to HTTP-only subscription</td>
    </tr>
            <tr>
    <td>https</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Message to send to HTTPS-only subscription</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Default message to send.</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</td>
    </tr>
            <tr>
    <td>sms</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Message to send to SMS-only subscription</td>
    </tr>
            <tr>
    <td>sqs</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Message to send to SQS-only subscription</td>
    </tr>
            <tr>
    <td>subject</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Subject line for email delivery.</td>
    </tr>
            <tr>
    <td>topic</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The topic you want to publish to.</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


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

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

