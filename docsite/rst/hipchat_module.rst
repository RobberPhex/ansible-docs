.. _hipchat:


hipchat - Send a message to hipchat
+++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Send a message to hipchat

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
    <td>api</td>
    <td>no</td>
    <td>https://api.hipchat.com/v1/rooms/message</td>
        <td><ul></ul></td>
        <td>API url if using a self-hosted hipchat server (added in Ansible 1.6.0)</td>
    </tr>
            <tr>
    <td>color</td>
    <td>no</td>
    <td>yellow</td>
        <td><ul><li>yellow</li><li>red</li><li>green</li><li>purple</li><li>gray</li><li>random</li></ul></td>
        <td>Background color for the message. Default is yellow.</td>
    </tr>
            <tr>
    <td>from</td>
    <td>no</td>
    <td>Ansible</td>
        <td><ul></ul></td>
        <td>Name the message will appear be sent from. max 15 characters. Over 15, will be shorten.</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The message body.</td>
    </tr>
            <tr>
    <td>msg_format</td>
    <td>no</td>
    <td>text</td>
        <td><ul><li>text</li><li>html</li></ul></td>
        <td>message format. html or text. Default is text.</td>
    </tr>
            <tr>
    <td>notify</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>notify or not (change the tab color, play a sound, etc)</td>
    </tr>
            <tr>
    <td>room</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>ID or name of the room.</td>
    </tr>
            <tr>
    <td>token</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>API token.</td>
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

    - hipchat: token=AAAAAA room=notify msg="Ansible task finished"



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

