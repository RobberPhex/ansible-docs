.. _pamd:


pamd - Manage PAM Modules
+++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Edit PAM service's type, control, module path and module arguments. In order for a PAM rule to be modified, the type, control and module_path must match an existing rule.  See man(5) pam.d for details.




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
                <tr><td>control<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The control of the PAM rule being modified.  This may be a complicated control with brackets.  If this is the case, be sure to put "[bracketed controls]" in quotes.  The type, control and module_path all must match a rule to be modified.</div>        </td></tr>
                <tr><td>module_arguments<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When state is 'updated', the module_arguments will replace existing module_arguments.  When state is 'args_absent' args matching those listed in module_arguments will be removed.  When state is 'args_present' any args listed in module_arguments are added if missing from the existing rule.  Furthermore, if the module argument takes a value denoted by '=', the value will be changed to that specified in module_arguments.</div>        </td></tr>
                <tr><td>module_path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The module path of the PAM rule being modified.  The type, control and module_path all must match a rule to be modified.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name generally refers to the PAM service file to change, for example system-auth.</div>        </td></tr>
                <tr><td>new_control<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The control to assign to the new rule.</div>        </td></tr>
                <tr><td>new_module_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The control to assign to the new rule.</div>        </td></tr>
                <tr><td>new_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The type to assign to the new rule.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/pam.d/</td>
        <td></td>
        <td><div>This is the path to the PAM service files</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>updated</td>
        <td><ul><li>updated</li><li>before</li><li>after</li><li>args_present</li><li>args_absent</li></ul></td>
        <td><div>The default of 'updated' will modify an existing rule if type, control and module_path all match an existing rule.  With 'before', the new rule will be inserted before a rule matching type, control and module_path.  Similarly, with 'after', the new rule will be inserted after an existing rule matching type, control and module_path.  With either 'before' or 'after' new_type, new_control, and new_module_path must all be specified.  If state is 'args_absent' or 'args_present', new_type, new_control, and new_module_path will be ignored.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The type of the PAM rule being modified.  The type, control and module_path all must match a rule to be modified.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Update pamd rule's control in /etc/pam.d/system-auth
      pamd:
        name: system-auth
        type: auth
        control: required
        module_path: pam_faillock.so
        new_control: sufficient
    
    - name: Update pamd rule's complex control in /etc/pam.d/system-auth
      pamd:
        name: system-auth
        type: session
        control: '[success=1 default=ignore]'
        module_path: pam_succeed_if.so
        new_control: '[success=2 default=ignore]'
    
    - name: Insert a new rule before an existing rule
      pamd:
        name: system-auth
        type: auth
        control: required
        module_path: pam_faillock.so
        new_type: auth
        new_control: sufficient
        new_module_path: pam_faillock.so
        state: before
    
    - name: Insert a new rule after an existing rule
      pamd:
        name: system-auth
        type: auth
        control: required
        module_path: pam_faillock.so
        new_type: auth
        new_control: sufficient
        new_module_path: pam_faillock.so
        state: after
    
    - name: Remove module arguments from an existing rule
      pamd:
        name: system-auth
        type: auth
        control: required
        module_path: pam_faillock.so
        module_arguments: ''
        state: updated
    
    - name: Replace all module arguments in an existing rule
      pamd:
        name: system-auth
        type: auth
        control: required
        module_path: pam_faillock.so
        module_arguments: 'preauth
            silent
            deny=3
            unlock_time=604800
            fail_interval=900'
        state: updated
    
    - name: Remove specific arguments from a rule
      pamd:
        name: system-auth
        type: session control='[success=1 default=ignore]'
        module_path: pam_succeed_if.so
        module_arguments: 'crond quiet'
        state: args_absent
    
    - name: Ensure specific arguments are present in a rule
      pamd:
        name: system-auth
        type: session
        control: '[success=1 default=ignore]'
        module_path: pam_succeed_if.so
        module_arguments: 'crond quiet'
        state: args_present
    
    - name: Update specific argument value in a rule
      pamd:
        name: system-auth
        type: auth
        control: required
        module_path: pam_faillock.so
        module_arguments: 'fail_interval=300'
        state: args_present

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> dest </td>
        <td> path to pam.d service that was changed </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> /etc/pam.d/system-auth </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
