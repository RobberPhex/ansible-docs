.. _win_domain_controller:


win_domain_controller - Manage domain controller/member server state for a Windows host
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Ensure that a Windows Server 2012+ host is configured as a domain controller or demoted to member server. This module may require subsequent use of the :ref:`win_reboot <win_reboot>` action if changes are made.




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
        <td><div>when <code>state</code> is <code>domain_controller</code>, the DNS name of the domain for which the targeted Windows host should be a DC</div>        </td></tr>
                <tr><td>domain_admin_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>password for the specified <code>domain_admin_user</code></div>        </td></tr>
                <tr><td>domain_admin_user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>username of a domain admin for the target domain (necessary to promote or demote a domain controller)</div>        </td></tr>
                <tr><td>local_admin_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>password to be assigned to the local <code>Administrator</code> user (required when <code>state</code> is <code>member_server</code>)</div>        </td></tr>
                <tr><td>safe_mode_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>safe mode password for the domain controller (required when <code>state</code> is <code>domain_controller</code>)</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>domain_controller</li><li>member_server</li></ul></td>
        <td><div>whether the target host should be a domain controller or a member server</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # ensure a server is a domain controller
    - hosts: winclient
      gather_facts: no
      tasks:
      - win_domain_controller:
          dns_domain_name: ansible.vagrant
          domain_admin_user: testguy@ansible.vagrant
          domain_admin_password: password123!
          safe_mode_password: password123!
          state: domain_controller
          log_path: c:\ansible_win_domain_controller.txt
    
    # ensure a server is not a domain controller
    # note that without an action wrapper, in the case where a DC is demoted,
    # the task will fail with a 401 Unauthorized, because the domain credential
    # becomes invalid to fetch the final output over WinRM. This requires win_async
    # with credential switching (or other clever credential-switching
    # mechanism to get the output and trigger the required reboot)
    - hosts: winclient
      gather_facts: no
      tasks:
      - win_domain_controller:
          domain_admin_user: testguy@ansible.vagrant
          domain_admin_password: password123!
          local_admin_password: password123!
          state: member_server
          log_path: c:\ansible_win_domain_controller.txt
    

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
