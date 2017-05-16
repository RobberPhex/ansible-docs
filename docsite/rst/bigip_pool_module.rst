.. _bigip_pool:


bigip_pool - Manages F5 BIG-IP LTM pools
++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Manages F5 BIG-IP LTM pools via iControl SOAP API

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
    <td>host</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pool member IP</td>
    </tr>
            <tr>
    <td>lb_method</td>
    <td>no</td>
    <td>round_robin</td>
        <td><ul><li>round_robin</li><li>ratio_member</li><li>least_connection_member</li><li>observed_member</li><li>predictive_member</li><li>ratio_node_address</li><li>least_connection_node_address</li><li>fastest_node_address</li><li>observed_node_address</li><li>predictive_node_address</li><li>dynamic_ratio</li><li>fastest_app_response</li><li>least_sessions</li><li>dynamic_ratio_member</li><li>l3_addr</li><li>unknown</li><li>weighted_least_connection_member</li><li>weighted_least_connection_node_address</li><li>ratio_session</li><li>ratio_least_connection_member</li><li>ratio_least_connection_node_address</li></ul></td>
        <td>Load balancing method (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>monitor_type</td>
    <td>no</td>
    <td></td>
        <td><ul><li>and_list</li><li>m_of_n</li></ul></td>
        <td>Monitor rule type when monitors &gt; 1 (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>monitors</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Monitor template name list. Always use the full path to the monitor. (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pool name</td>
    </tr>
            <tr>
    <td>partition</td>
    <td>no</td>
    <td>Common</td>
        <td><ul></ul></td>
        <td>Partition of pool/pool member</td>
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
    <td></td>
        <td><ul></ul></td>
        <td>Pool member port</td>
    </tr>
            <tr>
    <td>quorum</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Monitor quorum value when monitor_type is m_of_n (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>server</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>BIG-IP host</td>
    </tr>
            <tr>
    <td>service_down_action</td>
    <td>no</td>
    <td></td>
        <td><ul><li>none</li><li>reset</li><li>drop</li><li>reselect</li></ul></td>
        <td>Sets the action to take when node goes down in pool (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>slow_ramp_time</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Sets the ramp-up time (in seconds) to gradually ramp up the load on newly added or freshly detected up pool members (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Pool/pool member state</td>
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

    
    ## playbook task examples:
    
    ---
    # file bigip-test.yml
    # ...
    - hosts: localhost
      tasks:
      - name: Create pool
        local_action: >
          bigip_pool
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=present
          name=matthite-pool
          partition=matthite
          lb_method=least_connection_member
          slow_ramp_time=120
    
      - name: Modify load balancer method
        local_action: >
          bigip_pool
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=present
          name=matthite-pool
          partition=matthite
          lb_method=round_robin
    
    - hosts: bigip-test
      tasks:
      - name: Add pool member
        local_action: >
          bigip_pool
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=present
          name=matthite-pool
          partition=matthite
          host="{{ ansible_default_ipv4["address"] }}"
          port=80
    
      - name: Remove pool member from pool
        local_action: >
          bigip_pool
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=absent
          name=matthite-pool
          partition=matthite
          host="{{ ansible_default_ipv4["address"] }}"
          port=80
    
    - hosts: localhost
      tasks:
      - name: Delete pool
        local_action: >
          bigip_pool
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=absent
          name=matthite-pool
          partition=matthite
    

.. note:: Requires BIG-IP software version >= 11
.. note:: F5 developed module 'bigsuds' required (see http://devcentral.f5.com)
.. note:: Best run as a local_action in your playbook


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

