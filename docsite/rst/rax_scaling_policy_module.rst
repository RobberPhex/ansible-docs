.. _rax_scaling_policy:


rax_scaling_policy - Manipulate Rackspace Cloud Autoscale Scaling Policy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.7

Manipulate Rackspace Cloud Autoscale Scaling Policy

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
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rackspace API key (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>at</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The UTC time when this policy will be executed. The time must be formatted according to <code>yyyy-MM-dd'T'HH:mm:ss.SSS</code> such as <code>2013-05-19T08:07:08Z</code></td>
    </tr>
            <tr>
    <td>change</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The change, either as a number of servers or as a percentage, to make in the scaling group. If this is a percentage, you must set <em>is_percent</em> to <code>true</code> also.</td>
    </tr>
            <tr>
    <td>cooldown</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The period of time, in seconds, that must pass before any scaling can occur after the previous scaling. Must be an integer between 0 and 86400 (24 hrs).</td>
    </tr>
            <tr>
    <td>credentials</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</td>
    </tr>
            <tr>
    <td>cron</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The time when the policy will be executed, as a cron entry. For example, if this is parameter is set to <code>1 0 * * *</code></td>
    </tr>
            <tr>
    <td>desired_capacity</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The desired server capacity of the scaling the group; that is, how many servers should be in the scaling group.</td>
    </tr>
            <tr>
    <td>env</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a> (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>is_percent</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether the value in <em>change</em> is a percent value</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name to give the policy</td>
    </tr>
            <tr>
    <td>policy_type</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>webhook</li><li>schedule</li></ul></td>
        <td>The type of policy that will be executed for the current release.</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td>Region to create an instance in</td>
    </tr>
            <tr>
    <td>scaling_group</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the scaling group that this policy will be added to</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rackspace username (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>verify_ssl</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether or not to require SSL validation of API endpoints (added in Ansible 1.5)</td>
    </tr>
        </table>


.. note:: Requires pyrax


Examples
--------

.. raw:: html

    <br/>


::

    ---
    - hosts: localhost
      gather_facts: false
      connection: local
      tasks:
        - rax_scaling_policy:
            credentials: ~/.raxpub
            region: ORD
            at: '2013-05-19T08:07:08Z'
            change: 25
            cooldown: 300
            is_percent: true
            name: ASG Test Policy - at
            policy_type: schedule
            scaling_group: ASG Test
          register: asps_at
    
        - rax_scaling_policy:
            credentials: ~/.raxpub
            region: ORD
            cron: '1 0 * * *'
            change: 25
            cooldown: 300
            is_percent: true
            name: ASG Test Policy - cron
            policy_type: schedule
            scaling_group: ASG Test
          register: asp_cron
    
        - rax_scaling_policy:
            credentials: ~/.raxpub
            region: ORD
            cooldown: 300
            desired_capacity: 5
            name: ASG Test Policy - webhook
            policy_type: webhook
            scaling_group: ASG Test
          register: asp_webhook

.. note:: The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
.. note:: ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
.. note:: ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
.. note:: ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

