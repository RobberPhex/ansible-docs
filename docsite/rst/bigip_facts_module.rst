.. _bigip_facts:


bigip_facts - Collect facts from F5 BIG-IP devices
++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Collect facts from F5 BIG-IP devices via iControl SOAP API

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
    <td>filter</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Shell-style glob matching string used to filter fact keys. Not applicable for software and system_info fact categories.</td>
    </tr>
            <tr>
    <td>include</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>address_class</li><li>certificate</li><li>client_ssl_profile</li><li>device_group</li><li>interface</li><li>key</li><li>node</li><li>pool</li><li>rule</li><li>self_ip</li><li>software</li><li>system_info</li><li>traffic_group</li><li>trunk</li><li>virtual_address</li><li>virtual_server</li><li>vlan</li></ul></td>
        <td>Fact category or list of categories to collect</td>
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
    <td>session</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>BIG-IP session support; may be useful to avoid concurrency issues in certain circumstances.</td>
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
      - name: Collect BIG-IP facts
        local_action: >
          bigip_facts
          server=lb.mydomain.com
          user=admin
          password=mysecret
          include=interface,vlan
    

.. note:: Requires BIG-IP software version >= 11.4
.. note:: F5 developed module 'bigsuds' required (see http://devcentral.f5.com)
.. note:: Best run as a local_action in your playbook
.. note:: Tested with manager and above account privilege level


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

