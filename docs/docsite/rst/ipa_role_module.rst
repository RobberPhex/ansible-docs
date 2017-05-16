.. _ipa_role:


ipa_role - Manage FreeIPA role
++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add, modify and delete a role within FreeIPA server using FreeIPA API




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
                <tr><td>cn<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Role name.</div><div>Can not be changed as it is the unique identifier.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A description of this role-group.</div>        </td></tr>
                <tr><td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of group names assign to this role.</div><div>If an empty list is passed all assigned groups will be unassigned from the role.</div><div>If option is omitted groups will not be checked or changed.</div><div>If option is passed all assigned groups that are not passed will be unassigned from the role.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of host names to assign.</div><div>If an empty list is passed all assigned hosts will be unassigned from the role.</div><div>If option is omitted hosts will not be checked or changed.</div><div>If option is passed all assigned hosts that are not passed will be unassigned from the role.</div>        </td></tr>
                <tr><td>hostgroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of host group names to assign.</div><div>If an empty list is passed all assigned host groups will be removed from the role.</div><div>If option is omitted host groups will not be checked or changed.</div><div>If option is passed all assigned hostgroups that are not passed will be unassigned from the role.</div>        </td></tr>
                <tr><td>ipa_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ipa.example.com</td>
        <td></td>
        <td><div>IP or hostname of IPA server</div>        </td></tr>
                <tr><td>ipa_pass<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password of administrative user</div>        </td></tr>
                <tr><td>ipa_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>443</td>
        <td></td>
        <td><div>Port of IPA server</div>        </td></tr>
                <tr><td>ipa_prot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https</td>
        <td><ul><li>http</li><li>https</li></ul></td>
        <td><div>Protocol used by IPA server</div>        </td></tr>
                <tr><td>ipa_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Administrative account used on IPA server</div>        </td></tr>
                <tr><td>service<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of service names to assign.</div><div>If an empty list is passed all assigned services will be removed from the role.</div><div>If option is omitted services will not be checked or changed.</div><div>If option is passed all assigned services that are not passed will be removed from the role.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State to ensure</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of user names to assign.</div><div>If an empty list is passed all assigned users will be removed from the role.</div><div>If option is omitted users will not be checked or changed.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>This only applies if <code>ipa_prot</code> is <em>https</em>.</div><div>If set to <code>no</code>, the SSL certificates will not be validated.</div><div>This should only set to <code>no</code> used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure role is present
    - ipa_role:
        name: dba
        description: Database Administrators
        state: present
        user:
        - pinky
        - brain
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure role with certain details
    - ipa_role:
        name: another-role
        description: Just another role
        group:
        - editors
        host:
        - host01.example.com
        hostgroup:
        - hostgroup01
        service:
        - service01
    
    # Ensure role is absent
    - ipa_role:
        name: dba
        state: absent
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret

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
        <td> role </td>
        <td> Role as returned by IPA API. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center>  </td>
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
