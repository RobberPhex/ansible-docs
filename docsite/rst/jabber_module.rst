.. _jabber:


jabber - Send a message to jabber user or chat room
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Send a message to jabber

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
    <td>encoding</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>message encoding</td>
    </tr>
            <tr>
    <td>host</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>host to connect, overrides user info</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The message body.</td>
    </tr>
            <tr>
    <td>password</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>password for user to connect</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>5222</td>
        <td><ul></ul></td>
        <td>port to connect to, overrides default</td>
    </tr>
            <tr>
    <td>to</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>user ID or name of the room, when using room use a slash to indicate your nick.</td>
    </tr>
            <tr>
    <td>user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>User as which to connect</td>
    </tr>
        </table>


.. note:: Requires xmpp


Examples
--------

.. raw:: html

    <br/>


::

    # send a message to a user
    - jabber: user=mybot@example.net
              password=secret
              to=friend@example.net
              msg="Ansible task finished"
    
    # send a message to a room
    - jabber: user=mybot@example.net
              password=secret
              to=mychaps@conference.example.net/ansiblebot
              msg="Ansible task finished"
    
    # send a message, specifying the host and port
    - jabber user=mybot@example.net
             host=talk.example.net
             port=5223
             password=secret
             to=mychaps@example.net
             msg="Ansible task finished"



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

