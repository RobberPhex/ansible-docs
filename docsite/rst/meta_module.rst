.. _meta:


meta - Execute Ansible 'actions'
++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Meta tasks are a special kind of task which can influence Ansible internal execution or state. Prior to Ansible 2.0, the only meta option available was `flush_handlers`. As of 2.2, there are five meta tasks which can be used. Meta tasks can be used anywhere within your playbook.




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
    <td>free_form<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>noop</li><li>flush_handlers</li><li>refresh_inventory</li><li>clear_facts</li><li>clear_host_errors</li><li>end_play</li></ul></td>
        <td><div>This module takes a free form command, as a string. There's not an actual option named "free form".  See the examples!</div><div><code>flush_handlers</code> makes Ansible run any handler tasks which have thus far been notified. Ansible inserts these tasks internally at certain points to implicitly trigger handler runs (after pre/post tasks, the final role execution, and the main tasks section of your plays).</div><div><code>refresh_inventory</code> (added in 2.0) forces the reload of the inventory, which in the case of dynamic inventory scripts means they will be re-executed. This is mainly useful when additional hosts are created and users wish to use them instead of using the `add_host` module.</div><div><code>noop</code> (added in 2.0) This literally does 'nothing'. It is mainly used internally and not recommended for general use.</div><div><code>clear_facts</code> (added in 2.1) causes the gathered facts for the hosts specified in the play's list of hosts to be cleared, including the fact cache.</div><div><code>clear_host_errors</code> (added in 2.1) clears the failed state (if any) from hosts specified in the play's list of hosts.</div><div><code>end_play</code> (added in 2.2) causes the play to end without failing the host.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # force all notified handlers to run at this point, not waiting for normal sync points
    - template: src=new.j2 dest=/etc/config.txt
      notify: myhandler
    - meta: flush_handlers
    
    # reload inventory, useful with dynamic inventories when play makes changes to the existing hosts
    - cloud_guest: name=newhost state=present # this is fake module
    - meta: refresh_inventory
    
    # clear gathered facts from all currently targeted hosts
    - meta: clear_facts
    
    # bring host back to play after failure
    - copy: src=file dest=/etc/file
      remote_user: imightnothavepermission
    - meta: clear_host_errors


Notes
-----

.. note:: meta is not really a module nor action_plugin as such it cannot be overwritten.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

