.. _bigip_pool_member:


bigip_pool_member - Manages F5 BIG-IP LTM pool members
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Manages F5 BIG-IP LTM pool members via iControl SOAP API

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
    <td>connection_limit</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pool member connection limit. Setting this to 0 disables the limit.</td>
    </tr>
            <tr>
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pool member description</td>
    </tr>
            <tr>
    <td>host</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pool member IP</td>
    </tr>
            <tr>
    <td>partition</td>
    <td>no</td>
    <td>Common</td>
        <td><ul></ul></td>
        <td>Partition</td>
    </tr>
            <tr>
    <td>password</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>BIG-IP password</td>
    </tr>
            <tr>
    <td>pool</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pool name. This pool must exist.</td>
    </tr>
            <tr>
    <td>port</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pool member port</td>
    </tr>
            <tr>
    <td>rate_limit</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pool member rate limit (connections-per-second). Setting this to 0 disables the limit.</td>
    </tr>
            <tr>
    <td>ratio</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pool member ratio weight. Valid values range from 1 through 100. New pool members -- unless overriden with this value -- default to 1.</td>
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
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Pool member state</td>
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
    - hosts: bigip-test
      tasks:
      - name: Add pool member
        local_action: >
          bigip_pool_member
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=present
          pool=matthite-pool
          partition=matthite
          host="{{ ansible_default_ipv4["address"] }}"
          port=80
          description="web server"
          connection_limit=100
          rate_limit=50
          ratio=2
    
      - name: Modify pool member ratio and description
        local_action: >
          bigip_pool_member
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=present
          pool=matthite-pool
          partition=matthite
          host="{{ ansible_default_ipv4["address"] }}"
          port=80
          ratio=1
          description="nginx server"
    
      - name: Remove pool member from pool
        local_action: >
          bigip_pool_member
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=absent
          pool=matthite-pool
          partition=matthite
          host="{{ ansible_default_ipv4["address"] }}"
          port=80
    

.. note:: Requires BIG-IP software version >= 11
.. note:: F5 developed module 'bigsuds' required (see http://devcentral.f5.com)
.. note:: Best run as a local_action in your playbook
.. note:: Supersedes bigip_pool for managing pool members


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

