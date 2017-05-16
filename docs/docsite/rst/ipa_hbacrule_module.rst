.. _ipa_hbacrule:


ipa_hbacrule - Manage FreeIPA HBAC rule
+++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add, modify or delete an IPA HBAC rule using IPA API.




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
        <td><div>Canonical name.</div><div>Can not be changed as it is the unique identifier.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of host names to assign.</div><div>If an empty list is passed all hosts will be removed from the rule.</div><div>If option is omitted hosts will not be checked or changed.</div>        </td></tr>
                <tr><td>hostcategory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li></ul></td>
        <td><div>Host category</div>        </td></tr>
                <tr><td>hostgroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of hostgroup names to assign.</div><div>If an empty list is passed all hostgroups will be removed. from the rule</div><div>If option is omitted hostgroups will not be checked or changed.</div>        </td></tr>
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
        <td><div>List of service names to assign.</div><div>If an empty list is passed all services will be removed from the rule.</div><div>If option is omitted services will not be checked or changed.</div>        </td></tr>
                <tr><td>servicecategory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li></ul></td>
        <td><div>Service category</div>        </td></tr>
                <tr><td>servicegroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of service group names to assign.</div><div>If an empty list is passed all assigned service groups will be removed from the rule.</div><div>If option is omitted service groups will not be checked or changed.</div>        </td></tr>
                <tr><td>sourcehost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of source host names to assign.</div><div>If an empty list if passed all assigned source hosts will be removed from the rule.</div><div>If option is omitted source hosts will not be checked or changed.</div>        </td></tr>
                <tr><td>sourcehostcategory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li></ul></td>
        <td><div>Source host category</div>        </td></tr>
                <tr><td>sourcehostgroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of source host group names to assign.</div><div>If an empty list if passed all assigned source host groups will be removed from the rule.</div><div>If option is omitted source host groups will not be checked or changed.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>enabled</li><li>disabled</li></ul></td>
        <td><div>State to ensure</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of user names to assign.</div><div>If an empty list if passed all assigned users will be removed from the rule.</div><div>If option is omitted users will not be checked or changed.</div>        </td></tr>
                <tr><td>usercategory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li></ul></td>
        <td><div>User category</div>        </td></tr>
                <tr><td>usergroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of user group names to assign.</div><div>If an empty list if passed all assigned user groups will be removed from the rule.</div><div>If option is omitted user groups will not be checked or changed.</div>        </td></tr>
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

    # Ensure rule to allow all users to access any host from any host
    - ipa_hbacrule:
        name: allow_all
        description: Allow all users to access any host from any host
        hostcategory: all
        servicecategory: all
        usercategory: all
        state: present
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure rule with certain limitations
    - ipa_hbacrule:
        name: allow_all_developers_access_to_db
        description: Allow all developers to access any database from any host
        hostgroup:
        - db-server
        usergroup:
        - developers
        state: present
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure rule is absent
    - ipa_hbacrule:
        name: rule_to_be_deleted
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
        <td> hbacrule </td>
        <td> HBAC rule as returned by IPA API. </td>
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
