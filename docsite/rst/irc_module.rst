.. _irc:


irc - Send a message to an IRC channel
++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Send a message to an IRC channel. This is a very simplistic implementation.

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
    <td>channel</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Channel name</td>
    </tr>
            <tr>
    <td>color</td>
    <td>no</td>
    <td>none</td>
        <td><ul><li>none</li><li>yellow</li><li>red</li><li>green</li><li>blue</li><li>black</li></ul></td>
        <td>Text color for the message. ("none" is a valid option in 1.6 or later, in 1.6 and prior, the default color is black, not "none").</td>
    </tr>
            <tr>
    <td>key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Channel key (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The message body.</td>
    </tr>
            <tr>
    <td>nick</td>
    <td>no</td>
    <td>ansible</td>
        <td><ul></ul></td>
        <td>Nickname. May be shortened, depending on server's NICKLEN setting.</td>
    </tr>
            <tr>
    <td>passwd</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Server password</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>6667</td>
        <td><ul></ul></td>
        <td>IRC server port number</td>
    </tr>
            <tr>
    <td>server</td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td>IRC server name/address</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td>Timeout to use while waiting for successful registration and join messages, this is to prevent an endless loop (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>use_ssl</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Designates whether TLS/SSL should be used when connecting to the IRC server (added in Ansible 1.8)</td>
    </tr>
        </table>


.. note:: Requires socket


Examples
--------

.. raw:: html

    <br/>


::

    - irc: server=irc.example.net channel="#t1" msg="Hello world"
    
    - local_action: irc port=6669
                    channel="#t1"
                    msg="All finished at {{ ansible_date_time.iso8601 }}"
                    color=red
                    nick=ansibleIRC



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

