.. _flowdock:


flowdock - Send a message to a flowdock
+++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Send a message to a flowdock team inbox or chat using the push API (see https://www.flowdock.com/api/team-inbox and https://www.flowdock.com/api/chat)

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
    <td>external_user_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(chat only - required) Name of the "user" sending the message</td>
    </tr>
            <tr>
    <td>from_address</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(inbox only - required) Email address of the message sender</td>
    </tr>
            <tr>
    <td>from_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(inbox only) Name of the message sender</td>
    </tr>
            <tr>
    <td>link</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(inbox only) Link associated with the message. This will be used to link the message subject in Team Inbox.</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Content of the message</td>
    </tr>
            <tr>
    <td>project</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(inbox only) Human readable identifier for more detailed message categorization</td>
    </tr>
            <tr>
    <td>reply_to</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(inbox only) Email address for replies</td>
    </tr>
            <tr>
    <td>source</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(inbox only - required) Human readable identifier of the application that uses the Flowdock API</td>
    </tr>
            <tr>
    <td>subject</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(inbox only - required) Subject line of the message</td>
    </tr>
            <tr>
    <td>tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>tags of the message, separated by commas</td>
    </tr>
            <tr>
    <td>token</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>API token.</td>
    </tr>
            <tr>
    <td>type</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>inbox</li><li>chat</li></ul></td>
        <td>Whether to post to 'inbox' or 'chat'</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates. (added in Ansible 1.5.1)</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - flowdock: type=inbox
                token=AAAAAA
                from_address=user@example.com
                source='my cool app'
                msg='test from ansible'
                subject='test subject'
    
    - flowdock: type=chat
                token=AAAAAA
                external_user_name=testuser
                msg='test from ansible'
                tags=tag1,tag2,tag3



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

