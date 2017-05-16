.. _bigip_node:


bigip_node - Manages F5 BIG-IP LTM nodes
++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Manages F5 BIG-IP LTM nodes via iControl SOAP API

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
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Node description.</td>
    </tr>
            <tr>
    <td>host</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Node IP. Required when state=present and node does not exist. Error when state=absent.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Node name</td>
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
      - name: Add node
        local_action: >
          bigip_node
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=present
          partition=matthite
          host="{{ ansible_default_ipv4["address"] }}"
          name="{{ ansible_default_ipv4["address"] }}"
    
    # Note that the BIG-IP automatically names the node using the
    # IP address specified in previous play's host parameter.
    # Future plays referencing this node no longer use the host
    # parameter but instead use the name parameter.
    # Alternatively, you could have specified a name with the
    # name parameter when state=present.
    
      - name: Modify node description
        local_action: >
          bigip_node
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=present
          partition=matthite
          name="{{ ansible_default_ipv4["address"] }}"
          description="Our best server yet"
    
      - name: Delete node
        local_action: >
          bigip_node
          server=lb.mydomain.com
          user=admin
          password=mysecret
          state=absent
          partition=matthite
          name="{{ ansible_default_ipv4["address"] }}"
    

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

