.. _debug:


debug - Print statements during execution
+++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


This module prints statements during execution and can be useful for debugging variables or expressions without necessarily halting the playbook. Useful for debugging together with the 'when:' directive.

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
    <td>msg</td>
    <td>no</td>
    <td>Hello world!</td>
        <td><ul></ul></td>
        <td>The customized message that is printed. If omitted, prints a generic message.</td>
    </tr>
            <tr>
    <td>var</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A variable name to debug.  Mutually exclusive with the 'msg' option.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example that prints the loopback address and gateway for each host
    - debug: msg="System {{ inventory_hostname }} has uuid {{ ansible_product_uuid }}"
    
    - debug: msg="System {{ inventory_hostname }} has gateway {{ ansible_default_ipv4.gateway }}"
      when: ansible_default_ipv4.gateway is defined
    
    - shell: /usr/bin/uptime
      register: result
    
    - debug: var=result
    
    - name: Display all variables/facts known for a host
      debug: var=hostvars[inventory_hostname]



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

