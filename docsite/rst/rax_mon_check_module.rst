.. _rax_mon_check:


rax_mon_check - Create or delete a Rackspace Cloud Monitoring check for an existing entity.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create or delete a Rackspace Cloud Monitoring check associated with an existing rax_mon_entity. A check is a specific test or measurement that is performed, possibly from different monitoring zones, on the systems you monitor. Rackspace monitoring module flow | rax_mon_entity -> *rax_mon_check* -> rax_mon_notification -> rax_mon_notification_plan -> rax_mon_alarm


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * pyrax


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
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Rackspace API key (overrides <em>credentials</em>)</div></br>
        <div style="font-size: small;">aliases: password<div></td></tr>
            <tr>
    <td>auth_endpoint<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>https://identity.api.rackspacecloud.com/v2.0/</td>
        <td><ul></ul></td>
        <td><div>The URI of the authentication service</div></td></tr>
            <tr>
    <td>check_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>remote.dns</li><li>remote.ftp-banner</li><li>remote.http</li><li>remote.imap-banner</li><li>remote.mssql-banner</li><li>remote.mysql-banner</li><li>remote.ping</li><li>remote.pop3-banner</li><li>remote.postgresql-banner</li><li>remote.smtp-banner</li><li>remote.smtp</li><li>remote.ssh</li><li>remote.tcp</li><li>remote.telnet-banner</li><li>agent.filesystem</li><li>agent.memory</li><li>agent.load_average</li><li>agent.cpu</li><li>agent.disk</li><li>agent.network</li><li>agent.plugin</li></ul></td>
        <td><div>The type of check to create. <code>remote.</code> checks may be created on any rax_mon_entity. <code>agent.</code> checks may only be created on rax_mon_entities that have a non-null <code>agent_id</code>.</div></td></tr>
            <tr>
    <td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</div></br>
        <div style="font-size: small;">aliases: creds_file<div></td></tr>
            <tr>
    <td>details<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Additional details specific to the check type. Must be a hash of strings between 1 and 255 characters long, or an array or object containing 0 to 256 items.</div></td></tr>
            <tr>
    <td>disabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If "yes", ensure the check is created, but don't actually use it yet.</div></td></tr>
            <tr>
    <td>entity_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>ID of the rax_mon_entity to target with this check.</div></td></tr>
            <tr>
    <td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a></div></td></tr>
            <tr>
    <td>identity_type<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>rackspace</td>
        <td><ul></ul></td>
        <td><div>Authentication machanism to use, such as rackspace or keystone</div></td></tr>
            <tr>
    <td>label<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Defines a label for this check, between 1 and 64 characters long.</div></td></tr>
            <tr>
    <td>metadata<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Hash of arbitrary key-value pairs to accompany this check if it fires. Keys and values must be strings between 1 and 255 characters long.</div></td></tr>
            <tr>
    <td>monitoring_zones_poll<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Comma-separated list of the names of the monitoring zones the check should run from. Available monitoring zones include mzdfw, mzhkg, mziad, mzlon, mzord and mzsyd. Required for remote.* checks; prohibited for agent.* checks.</div></td></tr>
            <tr>
    <td>period<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The number of seconds between each time the check is performed. Must be greater than the minimum period set on your account.</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td><div>Region to create an instance in</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Ensure that a check with this <code>label</code> exists or does not exist.</div></td></tr>
            <tr>
    <td>target_alias<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>One of `target_alias` and `target_hostname` is required for remote.* checks, but prohibited for agent.* checks. Use the corresponding key in the entity's `ip_addresses` hash to resolve an IP address to target.</div></td></tr>
            <tr>
    <td>target_hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>One of `target_hostname` and `target_alias` is required for remote.* checks, but prohibited for agent.* checks. The hostname this check should target. Must be a valid IPv4, IPv6, or FQDN.</div></td></tr>
            <tr>
    <td>tenant_id<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The tenant ID used for authentication</div></td></tr>
            <tr>
    <td>tenant_name<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The tenant name used for authentication</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The number of seconds this check will wait when attempting to collect results. Must be less than the period.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Rackspace username (overrides <em>credentials</em>)</div></td></tr>
            <tr>
    <td>verify_ssl<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether or not to require SSL validation of API endpoints</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a monitoring check
      gather_facts: False
      hosts: local
      connection: local
      tasks:
      - name: Associate a check with an existing entity.
        rax_mon_check:
          credentials: ~/.rax_pub
          state: present
          entity_id: "{{ the_entity['entity']['id'] }}"
          label: the_check
          check_type: remote.ping
          monitoring_zones_poll: mziad,mzord,mzdfw
          details:
            count: 10
          meta:
            hurf: durf
        register: the_check


Notes
-----

.. note:: The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
.. note:: ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
.. note:: ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
.. note:: ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

