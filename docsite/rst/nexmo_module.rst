.. _nexmo:


nexmo - Send a SMS via nexmo
++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Send a SMS message via nexmo

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
    <td>api_key</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Nexmo API Key</td>
    </tr>
            <tr>
    <td>api_secret</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Nexmo API Secret</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Phone number(s) to send SMS message to</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Message to text to send. Messages longer than 160 characters will be split into multiple messages</td>
    </tr>
            <tr>
    <td>src</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Nexmo Number to send from</td>
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

    - name: Send notification message via Nexmo
      local_action:
        module: nexmo
        api_key: 640c8a53
        api_secret: 0ce239a6
        src: 12345678901
        dest:
          - 10987654321
          - 16789012345
        msg: "{{ inventory_hostname }} completed"



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

