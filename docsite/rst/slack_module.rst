.. _slack:


slack - Send Slack notifications
++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

The ``slack`` module sends notifications to http://slack.com via the Incoming WebHook integration

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
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Channel to send the message to. If absent, the message goes to the channel selected for the <em>token</em>.</td>
    </tr>
            <tr>
    <td>domain</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Slack (sub)domain for your environment without protocol. (i.e. <code>future500.slack.com</code>)</td>
    </tr>
            <tr>
    <td>icon_emoji</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Emoji for the message sender. See Slack documentation for options. (if <em>icon_emoji</em> is set, <em>icon_url</em> will not be used)</td>
    </tr>
            <tr>
    <td>icon_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url for the message sender's icon (default <code>http://www.ansible.com/favicon.ico</code>)</td>
    </tr>
            <tr>
    <td>link_names</td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>1</li><li>0</li></ul></td>
        <td>Automatically create links for channels and usernames in <em>msg</em>.</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Message to send.</td>
    </tr>
            <tr>
    <td>parse</td>
    <td>no</td>
    <td></td>
        <td><ul><li>full</li><li>none</li></ul></td>
        <td>Setting for the message parser at Slack</td>
    </tr>
            <tr>
    <td>token</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Slack integration token</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td>ansible</td>
        <td><ul></ul></td>
        <td>This is the sender of the message.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - name: Send notification message via Slack
      local_action:
        module: slack
        domain: future500.slack.com
        token: thetokengeneratedbyslack
        msg: "{{ inventory_hostname }} completed"
    
    - name: Send notification message via Slack all options
      local_action:
        module: slack
        domain: future500.slack.com
        token: thetokengeneratedbyslack
        msg: "{{ inventory_hostname }} completed"
        channel: "#ansible"
        username: "Ansible on {{ inventory_hostname }}"
        icon_url: "http://www.example.com/some-image-file.png"
        link_names: 0
        parse: 'none'
    



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

