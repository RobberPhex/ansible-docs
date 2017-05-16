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
    <td>attach</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A space-separated list of pathnames of files to attach to the message. Attached files will have their content-type set to <code>application/octet-stream</code>. (added in Ansible 1.0)</td>
    </tr>
            <tr>
    <td>bcc</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The email-address(es) the mail is being 'blind' copied to. This is a comma-separated list, which may contain address and phrase portions.</td>
    </tr>
            <tr>
    <td>body</td>
    <td>no</td>
    <td>$subject</td>
        <td><ul></ul></td>
        <td>The body of the email being sent.</td>
    </tr>
            <tr>
    <td>cc</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The email-address(es) the mail is being copied to. This is a comma-separated list, which may contain address and phrase portions.</td>
    </tr>
            <tr>
    <td>charset</td>
    <td>no</td>
    <td>us-ascii</td>
        <td><ul></ul></td>
        <td>The character set of email being sent</td>
    </tr>
            <tr>
    <td>from</td>
    <td>no</td>
    <td>root</td>
        <td><ul></ul></td>
        <td>The email-address the mail is sent from. May contain address and phrase.</td>
    </tr>
            <tr>
    <td>headers</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A vertical-bar-separated list of headers which should be added to the message. Each individual header is specified as <code>header=value</code> (see example below). (added in Ansible 1.0)</td>
    </tr>
            <tr>
    <td>host</td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td>The mail server</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>25</td>
        <td><ul></ul></td>
        <td>The mail server port (added in Ansible 1.0)</td>
    </tr>
            <tr>
    <td>subject</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The subject of the email being sent.</td>
    </tr>
            <tr>
    <td>to</td>
    <td>no</td>
    <td>root</td>
        <td><ul></ul></td>
        <td>The email-address(es) the mail is being sent to. This is a comma-separated list, which may contain address and phrase portions.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example playbook sending mail to root
    - local_action: mail msg='System {{ ansible_hostname }} has been successfully provisioned.'
    
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



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

