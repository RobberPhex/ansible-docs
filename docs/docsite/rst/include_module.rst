.. _include:


include - include a play or task list.
++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Includes a file with a list of plays or tasks to be executed in the current playbook.
* Files with a list of plays can only be included at the top level, lists of tasks can only be included where tasks normally run (in play).
* Before 2.0 all includes were 'static', executed at play compile time.
* Static includes are not subject to most directives, for example, loops or conditionals, they are applied instead to each inherited task.
* Since 2.0 task includes are dynamic and behave more like real tasks.  This means they can be looped, skipped and use variables from any source. Ansible tries to auto detect this, use the `static` directive (new in 2.1) to bypass autodetection.




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
                <tr><td>free-form<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This module allows you to specify the name of the file directly w/o any other options.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # include a play after another play
    - hosts: localhost
      tasks:
        - debug:
            msg: "play1"
    
    - include: otherplays.yml
    
    
    # include task list in play
    - hosts: all
      tasks:
        - debug:
            msg: task1
    
        - include: stuff.yml
    
        - debug:
            msg: task10
    
    # dyanmic include task list in play
    - hosts: all
      tasks:
        - debug:
            msg: task1
    
        - include: "{{ hostvar }}.yml"
          static: no
          when: hostvar is defined


Notes
-----

.. note::
    - This is really not a module, though it appears as such, this is a feature of the Ansible Engine, as such it cannot be overridden the same way a module can.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
