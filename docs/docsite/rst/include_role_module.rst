.. _include_role:


include_role - Load and execute a role
++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Loads and executes a role as a task, this frees roles from the `role:` directive and allows them to be treated more as tasks.




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
                <tr><td>allow_duplicates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Overrides the role's metadata setting to allow using a role more than once with the same parameters.</div>        </td></tr>
                <tr><td>defaults_from<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>main</td>
        <td></td>
        <td><div>File to load from a Role's defaults/ directory.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the role to be executed.</div>        </td></tr>
                <tr><td>private<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>If True the variables from defaults/ and vars/ in a role will not be made available to the rest of the play.</div>        </td></tr>
                <tr><td>tasks_from<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>main</td>
        <td></td>
        <td><div>File to load from a Role's tasks/ directory.</div>        </td></tr>
                <tr><td>vars_from<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>main</td>
        <td></td>
        <td><div>File to load from a Role's vars/ directory.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - include_role:
        name: myrole
    
    - name: Run tasks/other.yml instead of 'main'
      include_role:
        name: myrole
        tasks_from: other
    
    - name: Pass variables to role
      include_role:
        name: myrole
      vars:
        rolevar1: 'value from task'
    
    - name: Use role in loop
      include_role:
        name: myrole
      with_items:
        - '{{ roleinput1 }}'
        - '{{ roleinput2 }}'
      loop_control:
        loop_var: roleinputvar
    
    - name: conditional role
      include_role:
        name: myrole
      when: not idontwanttorun


Notes
-----

.. note::
    - Handlers are made available to the whole play.
    - simple dependencies seem to work fine.
    - As with ``include`` this task can be static or dynamic, If static it implies that it won't need templating nor loops nor conditionals and will show included tasks in the --list options. Ansible will try to autodetect what is needed, but you can set `static` to `yes` or `no` at task level to control this.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
