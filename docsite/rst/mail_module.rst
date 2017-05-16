.. _mail:


mail - Send an email
++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module is useful for sending emails from playbooks.
One may wonder why automate sending emails?  In complex environments there are from time to time processes that cannot be automated, either because you lack the authority to make it so, or because not everyone agrees to a common approach.
If you cannot automate a specific step, but the step is non-blocking, sending out an email to the responsible party to make him perform his part of the bargain is an elegant way to put the responsibility in someone else's lap.
Of course sending out a mail can be equally useful as a way to notify one or more people in a team that a specific action has been (successfully) taken.




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
    <td>attach<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A space-separated list of pathnames of files to attach to the message. Attached files will have their content-type set to <code>application/octet-stream</code>.</div></td></tr>
            <tr>
    <td>bcc<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The email-address(es) the mail is being 'blind' copied to. This is a comma-separated list, which may contain address and phrase portions.</div></td></tr>
            <tr>
    <td>body<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>$subject</td>
        <td><ul></ul></td>
        <td><div>The body of the email being sent.</div></td></tr>
            <tr>
    <td>cc<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The email-address(es) the mail is being copied to. This is a comma-separated list, which may contain address and phrase portions.</div></td></tr>
            <tr>
    <td>charset<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>us-ascii</td>
        <td><ul></ul></td>
        <td><div>The character set of email being sent</div></td></tr>
            <tr>
    <td>from<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>root</td>
        <td><ul></ul></td>
        <td><div>The email-address the mail is sent from. May contain address and phrase.</div></td></tr>
            <tr>
    <td>headers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A vertical-bar-separated list of headers which should be added to the message. Each individual header is specified as <code>header=value</code> (see example below).</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>The mail server</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If SMTP requires password</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>25</td>
        <td><ul></ul></td>
        <td><div>The mail server port</div></td></tr>
            <tr>
    <td>subject<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The subject of the email being sent.</div></td></tr>
            <tr>
    <td>subtype<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>plain</td>
        <td><ul></ul></td>
        <td><div>The minor mime type, can be either text or html. The major type is always text.</div></td></tr>
            <tr>
    <td>to<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>root</td>
        <td><ul></ul></td>
        <td><div>The email-address(es) the mail is being sent to. This is a comma-separated list, which may contain address and phrase portions.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If SMTP requires username</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example playbook sending mail to root
    - local_action: mail subject='System {{ ansible_hostname }} has been successfully provisioned.'
    
    # Sending an e-mail using Gmail SMTP servers
    - local_action: mail
                    host='smtp.gmail.com'
                    port=587
                    username=username@gmail.com
                    password='mysecret'
                    to="John Smith <john.smith@example.com>"
                    subject='Ansible-report'
                    body='System {{ ansible_hostname }} has been successfully provisioned.'
    
    # Send e-mail to a bunch of users, attaching files
    - local_action: mail
                    host='127.0.0.1'
                    port=2025
                    subject="Ansible-report"
                    body="Hello, this is an e-mail. I hope you like it ;-)"
                    from="jane@example.net (Jane Jolie)"
                    to="John Doe <j.d@example.org>, Suzie Something <sue@example.com>"
                    cc="Charlie Root <root@localhost>"
                    attach="/etc/group /tmp/pavatar2.png"
                    headers=Reply-To=john@example.com|X-Special="Something or other"
                    charset=utf8
    # Sending an e-mail using the remote machine, not the Ansible controller node
    - mail:
        host='localhost'
        port=25
        to="John Smith <john.smith@example.com>"
        subject='Ansible-report'
        body='System {{ ansible_hostname }} has been successfully provisioned.'




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

