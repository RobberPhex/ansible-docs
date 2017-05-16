.. _win_domain_membership:


win_domain_membership - Manage domain/workgroup membership for a Windows host
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages domain membership or workgroup membership for a Windows host. Also supports hostname changes. This module may require subsequent use of the :ref:`win_reboot <win_reboot>` action if changes are made.




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
                <tr><td>dns_domain_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>when <code>state</code> is <code>domain</code>, the DNS name of the domain to which the targeted Windows host should be joined</div>        </td></tr>
                <tr><td>domain_admin_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>password for the specified <code>domain_admin_user</code></div>        </td></tr>
                <tr><td>domain_admin_user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>username of a domain admin for the target domain (required to join or leave the domain)</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the desired hostname for the Windows host</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>domain</li><li>workgroup</li></ul></td>
        <td><div>whether the target host should be a member of a domain or workgroup</div>        </td></tr>
                <tr><td>workgroup_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>when <code>state</code> is <code>workgroup</code>, the name of the workgroup that the Windows host should be in</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # host should be a member of domain ansible.vagrant; module will ensure the hostname is mydomainclient
    # and will use the passed credentials to join domain if necessary.
    # Ansible connection should use local credentials if possible.
    # If a reboot is required, the second task will trigger one and wait until the host is available.
    - hosts: winclient
      gather_facts: no
      tasks:
      - win_domain_membership:
          dns_domain_name: ansible.vagrant
          hostname: mydomainclient
          domain_admin_user: testguy@ansible.vagrant
          domain_admin_password: password123!
          state: domain
        register: domain_state
    
      - win_reboot:
        when: domain_state.reboot_required
    
    
    
    # Host should be in workgroup mywg- module will use the passed credentials to clean-unjoin domain if possible.
    # Ansible connection should use local credentials if possible.
    # The domain admin credentials can be sourced from a vault-encrypted variable
    - hosts: winclient
      gather_facts: no
      tasks:
      - win_domain_membership:
          workgroup_name: mywg
          domain_admin_user: '{{ win_domain_admin_user }}'
          domain_admin_password: '{{ win_domain_admin_password }}'
          state: workgroup

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
        <td> reboot_required </td>
        <td> True if changes were made that require a reboot. </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
