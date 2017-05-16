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
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Hello world!</td>
        <td><ul></ul></td>
        <td><div>The customized message that is printed. If omitted, prints a generic message.</div></td></tr>
            <tr>
    <td>var<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A variable name to debug.  Mutually exclusive with the 'msg' option.</div></td></tr>
            <tr>
    <td>verbosity<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A number that controls when the debug is run, if you set to 3 it will only run debug when -vvv or above</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example that prints the loopback address and gateway for each host
    - debug: msg="System {{ inventory_hostname }} has uuid {{ ansible_product_uuid }}"
    
    - debug: msg="System {{ inventory_hostname }} has gateway {{ ansible_default_ipv4.gateway }}"
      when: ansible_default_ipv4.gateway is defined
    
    - shell: /usr/bin/uptime
      register: result
    
    - debug: var=result verbosity=2
    
    - name: Display all variables/facts known for a host
      debug: var=hostvars[inventory_hostname] verbosity=4




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

