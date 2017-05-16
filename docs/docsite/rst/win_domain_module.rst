.. _win_domain:


win_domain - Ensures the existence of a Windows domain.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Ensure that the domain named by ``dns_domain_name`` exists and is reachable. If the domain is not reachable, the domain is created in a new forest on the target Windows Server 2012R2+ host. This module may require subsequent use of the :ref:`win_reboot <win_reboot>` action if changes are made.




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
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the DNS name of the domain which should exist and be reachable or reside on the target Windows host</div>        </td></tr>
                <tr><td>safe_mode_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>safe mode password for the domain controller</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # ensure the named domain is reachable from the target host; if not, create the domain in a new forest residing on the target host
    - win_domain:
        dns_domain_name: ansible.vagrant
        safe_mode_password: password123!
    

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
