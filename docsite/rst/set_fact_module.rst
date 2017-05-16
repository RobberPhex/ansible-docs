.. _set_fact:


set_fact - Set host facts from a task
+++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows setting new variables.  Variables are set on a host-by-host basis just like facts discovered by the setup module.
These variables will be available to subsequent plays during an ansible-playbook run, but will not be saved across executions even if you use a fact cache.




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
    <td>key_value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>set_fact</code> module takes key=value pairs as variables to set in the playbook scope. Or alternatively, accepts complex arguments using the <code>args:</code> statement.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example setting host facts using key=value pairs, note that this always creates strings or booleans
    - set_fact: one_fact="something" other_fact="{{ local_var }}"
    
    # Example setting host facts using complex arguments
    - set_fact:
         one_fact: something
         other_fact: "{{ local_var * 2 }}"
         another_fact: "{{ some_registered_var.results | map(attribute='ansible_facts.some_fact') | list }}"
    
    # As of 1.8, Ansible will convert boolean strings ('true', 'false', 'yes', 'no')
    # to proper boolean values when using the key=value syntax, however it is still
    # recommended that booleans be set using the complex argument style:
    - set_fact:
        one_fact: true
        other_fact: false
    


Notes
-----

.. note:: The `var=value` notation can only create strings or booleans. If you want to create lists/arrays or dictionary/hashes use `var: [val1, val2]`


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

