.. _pagerduty:


pagerduty - Create PagerDuty maintenance windows
++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

This module will let you create PagerDuty maintenance windows

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
    <td>desc</td>
    <td>no</td>
    <td>Created by Ansible</td>
        <td><ul></ul></td>
        <td>Short description of maintenance window.</td>
    </tr>
            <tr>
    <td>hours</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>Length of maintenance window in hours.</td>
    </tr>
            <tr>
    <td>minutes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Maintenance window in minutes (this is added to the hours). (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>PagerDuty unique subdomain.</td>
    </tr>
            <tr>
    <td>passwd</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>PagerDuty user password.</td>
    </tr>
            <tr>
    <td>requester_id</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>ID of user making the request. Only needed when using a token and creating a maintenance_window. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>service</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>PagerDuty service ID.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>running</li><li>started</li><li>ongoing</li></ul></td>
        <td>Create a maintenance window or get a list of ongoing windows.</td>
    </tr>
            <tr>
    <td>token</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>A pagerduty token, generated on the pagerduty site. Can be used instead of user/passwd combination. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>PagerDuty user ID.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates. (added in Ansible 1.5.1)</td>
    </tr>
        </table>


.. note:: Requires PagerDuty API access


Examples
--------

.. raw:: html

    <br/>


::

    # List ongoing maintenance windows using a user/passwd
    - pagerduty: name=companyabc user=example@example.com passwd=password123 state=ongoing
    
    # List ongoing maintenance windows using a token
    - pagerduty: name=companyabc token=xxxxxxxxxxxxxx state=ongoing
    
    # Create a 1 hour maintenance window for service FOO123, using a user/passwd
    - pagerduty: name=companyabc
                 user=example@example.com
                 passwd=password123
                 state=running
                 service=FOO123
    
    # Create a 5 minute maintenance window for service FOO123, using a token
    - pagerduty: name=companyabc
                 token=xxxxxxxxxxxxxx
                 hours=0
                 minutes=5
                 state=running
                 service=FOO123
    
    
    # Create a 4 hour maintenance window for service FOO123 with the description "deployment".
    - pagerduty: name=companyabc
                 user=example@example.com
                 passwd=password123
                 state=running
                 service=FOO123
                 hours=4
                 desc=deployment

.. note:: This module does not yet have support to end maintenance windows.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

