.. _bigip_monitor_tcp:


bigip_monitor_tcp - Manages F5 BIG-IP LTM tcp monitors
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Manages F5 BIG-IP LTM tcp monitors via iControl SOAP API

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
    <td>interval</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>The interval specifying how frequently the monitor instance of this template will run. By default, this interval is used for up and down states. The default API setting is 5.</td>
    </tr>
            <tr>
    <td>ip</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>IP address part of the ipport definition. The default API setting is "0.0.0.0".</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Monitor name</td>
    </tr>
            <tr>
    <td>parent</td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>tcp_echo</li><li>tcp_half_open</li></ul></td>
        <td>The parent template of this monitor template</td>
    </tr>
            <tr>
    <td>parent_partition</td>
    <td>no</td>
    <td>Common</td>
        <td><ul></ul></td>
        <td>Partition for the parent monitor</td>
    </tr>
            <tr>
    <td>partition</td>
    <td>no</td>
    <td>Common</td>
        <td><ul></ul></td>
        <td>Partition for the monitor</td>
    </tr>
            <tr>
    <td>password</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>BIG-IP password</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>port address part op the ipport definition. The default API setting is 0.</td>
    </tr>
            <tr>
    <td>receive</td>
    <td>yes</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>The receive string for the monitor call</td>
    </tr>
            <tr>
    <td>send</td>
    <td>yes</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>The send string for the monitor call</td>
    </tr>
            <tr>
    <td>server</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>BIG-IP host</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Monitor state</td>
    </tr>
            <tr>
    <td>time_until_up</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>Specifies the amount of time in seconds after the first successful response before a node will be marked up. A value of 0 will cause a node to be marked up immediately after a valid response is received from the node. The default API setting is 0.</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>The number of seconds in which the node or service must respond to the monitor request. If the target responds within the set time period, it is considered up. If the target does not respond within the set time period, it is considered down. You can change this number to any number you want, however, it should be 3 times the interval number of seconds plus 1 second. The default API setting is 16.</td>
    </tr>
            <tr>
    <td>type</td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>TTYPE_TCP</li><li>TTYPE_TCP_ECHO</li><li>TTYPE_TCP_HALF_OPEN</li></ul></td>
        <td>The template type of this monitor template</td>
    </tr>
            <tr>
    <td>user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>BIG-IP username</td>
    </tr>
        </table>


.. note:: Requires bigsuds


Examples
--------

.. raw:: html

    <br/>


::

    
    - name: BIGIP F5 | Create TCP Monitor
      local_action:
        module:             bigip_monitor_tcp
        state:              present
        server:             "{{ f5server }}"
        user:               "{{ f5user }}"
        password:           "{{ f5password }}"
        name:               "{{ item.monitorname }}"
        type:               tcp
        send:               "{{ item.send }}"
        receive:            "{{ item.receive }}"
      with_items: f5monitors-tcp
    - name: BIGIP F5 | Create TCP half open Monitor
      local_action:
        module:             bigip_monitor_tcp
        state:              present
        server:             "{{ f5server }}"
        user:               "{{ f5user }}"
        password:           "{{ f5password }}"
        name:               "{{ item.monitorname }}"
        type:               tcp
        send:               "{{ item.send }}"
        receive:            "{{ item.receive }}"
      with_items: f5monitors-halftcp
    - name: BIGIP F5 | Remove TCP Monitor
      local_action:
        module:             bigip_monitor_tcp
        state:              absent
        server:             "{{ f5server }}"
        user:               "{{ f5user }}"
        password:           "{{ f5password }}"
        name:               "{{ monitorname }}"
      with_flattened:
      - f5monitors-tcp
      - f5monitors-halftcp
    

.. note:: Requires BIG-IP software version >= 11
.. note:: F5 developed module 'bigsuds' required (see http://devcentral.f5.com)
.. note:: Best run as a local_action in your playbook
.. note:: Monitor API documentation: https://devcentral.f5.com/wiki/iControl.LocalLB__Monitor.ashx


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

