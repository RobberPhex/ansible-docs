.. _rax_mon_alarm:


rax_mon_alarm - Create or delete a Rackspace Cloud Monitoring alarm.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or delete a Rackspace Cloud Monitoring alarm that associates an existing rax_mon_entity, rax_mon_check, and rax_mon_notification_plan with criteria that specify what conditions will trigger which levels of notifications. Rackspace monitoring module flow | rax_mon_entity -> rax_mon_check -> rax_mon_notification -> rax_mon_notification_plan -> *rax_mon_alarm*


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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace API key, overrides <em>credentials</em>.</div></br>
    <div style="font-size: small;">aliases: password<div>        </td></tr>
                <tr><td>auth_endpoint<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>https://identity.api.rackspacecloud.com/v2.0/</td>
        <td></td>
        <td><div>The URI of the authentication service.</div>        </td></tr>
                <tr><td>check_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>ID of the check that should be alerted on. May be acquired by registering the value of a rax_mon_check task.</div>        </td></tr>
                <tr><td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>File to find the Rackspace credentials in. Ignored if <em>api_key</em> and <em>username</em> are provided.</div></br>
    <div style="font-size: small;">aliases: creds_file<div>        </td></tr>
                <tr><td>criteria<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Alarm DSL that describes alerting conditions and their output states. Must be between 1 and 16384 characters long. See http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/alerts-language.html for a reference on the alerting language.</div>        </td></tr>
                <tr><td>disabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If yes, create this alarm, but leave it in an inactive state. Defaults to no.</div>        </td></tr>
                <tr><td>entity_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>ID of the entity this alarm is attached to. May be acquired by registering the value of a rax_mon_entity task.</div>        </td></tr>
                <tr><td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Environment as configured in <em>~/.pyrax.cfg</em>, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a>.</div>        </td></tr>
                <tr><td>identity_type<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>rackspace</td>
        <td></td>
        <td><div>Authentication mechanism to use, such as rackspace or keystone.</div>        </td></tr>
                <tr><td>label<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Friendly name for this alarm, used to achieve idempotence. Must be a String between 1 and 255 characters long.</div>        </td></tr>
                <tr><td>metadata<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Arbitrary key/value pairs to accompany the alarm. Must be a hash of String keys and values between 1 and 255 characters long.</div>        </td></tr>
                <tr><td>notification_plan_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>ID of the notification plan to trigger if this alarm fires. May be acquired by registering the value of a rax_mon_notification_plan task.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td></td>
        <td><div>Region to create an instance in.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Ensure that the alarm with this <code>label</code> exists or does not exist.</div>        </td></tr>
                <tr><td>tenant_id<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The tenant ID used for authentication.</div>        </td></tr>
                <tr><td>tenant_name<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The tenant name used for authentication.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace username, overrides <em>credentials</em>.</div>        </td></tr>
                <tr><td>verify_ssl<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not to require SSL validation of API endpoints.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Alarm example
      gather_facts: False
      hosts: local
      connection: local
      tasks:
      - name: Ensure that a specific alarm exists.
        rax_mon_alarm:
          credentials: ~/.rax_pub
          state: present
          label: uhoh
          entity_id: "{{ the_entity['entity']['id'] }}"
          check_id: "{{ the_check['check']['id'] }}"
          notification_plan_id: "{{ defcon1['notification_plan']['id'] }}"
          criteria: >
            if (rate(metric['average']) > 10) {
              return new AlarmStatus(WARNING);
            }
            return new AlarmStatus(OK);
        register: the_alarm


Notes
-----

.. note::
    - The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
    - ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
    - ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
    - ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
