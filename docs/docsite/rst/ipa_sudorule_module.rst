.. _ipa_sudorule:


ipa_sudorule - Manage FreeIPA sudo rule
+++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add, modify or delete sudo rule within IPA server using IPA API.




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
                <tr><td>cmd<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of commands assigned to the rule.</div><div>If an empty list is passed all commands will be removed from the rule.</div><div>If option is omitted commands will not be checked or changed.</div>        </td></tr>
                <tr><td>cmdcategory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li></ul></td>
        <td><div>Command category the rule applies to.</div>        </td></tr>
                <tr><td>cn<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Canonical name.</div><div>Can not be changed as it is the unique identifier.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of hosts assigned to the rule.</div><div>If an empty list is passed all hosts will be removed from the rule.</div><div>If option is omitted hosts will not be checked or changed.</div><div>Option <code>hostcategory</code> must be omitted to assign hosts.</div>        </td></tr>
                <tr><td>hostcategory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li></ul></td>
        <td><div>Host category the rule applies to.</div><div>If 'all' is passed one must omit <code>host</code> and <code>hostgroup</code>.</div><div>Option <code>host</code> and <code>hostgroup</code> must be omitted to assign 'all'.</div>        </td></tr>
                <tr><td>hostgroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of host groups assigned to the rule.</div><div>If an empty list is passed all host groups will be removed from the rule.</div><div>If option is omitted host groups will not be checked or changed.</div><div>Option <code>hostcategory</code> must be omitted to assign host groups.</div>        </td></tr>
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
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>enabled</li><li>disabled</li></ul></td>
        <td><div>State to ensure</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of users assigned to the rule.</div><div>If an empty list is passed all users will be removed from the rule.</div><div>If option is omitted users will not be checked or changed.</div>        </td></tr>
                <tr><td>usercategory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>all</li></ul></td>
        <td><div>User category the rule applies to.</div>        </td></tr>
                <tr><td>usergroup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of user groups assigned to the rule.</div><div>If an empty list is passed all user groups will be removed from the rule.</div><div>If option is omitted user groups will not be checked or changed.</div>        </td></tr>
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

    # Ensure sudo rule is present thats allows all every body to execute any command on any host without beeing asked for a password.
    - ipa_sudorule:
        name: sudo_all_nopasswd
        cmdcategory: all
        description: Allow to run every command with sudo without password
        hostcategory: all
        sudoopt:
        - '!authenticate'
        usercategory: all
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    # Ensure user group developers can run every command on host group db-server as well as on host db01.example.com.
    - ipa_sudorule:
        name: sudo_dev_dbserver
        description: Allow developers to run every command with sudo on all database server
        cmdcategory: all
        host:
        - db01.example.com
        hostgroup:
        - db-server
        sudoopt:
        - '!authenticate'
        usergroup:
        - developers
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
        <td> sudorule </td>
        <td> Sudorule as returned by IPA </td>
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
