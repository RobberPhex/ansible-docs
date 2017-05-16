.. _ipa_group:


ipa_group - Manage FreeIPA group
++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add, modify and delete group within IPA server




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
                <tr><td>external<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Allow adding external non-IPA members from trusted domains.</div>        </td></tr>
                <tr><td>gidnumber<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>GID (use this option to set it manually).</div>        </td></tr>
                <tr><td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of group names assigned to this group.</div><div>If an empty list is passed all groups will be removed from this group.</div><div>If option is omitted assigned groups will not be checked or changed.</div><div>Groups that are already assigned but not passed will be removed.</div>        </td></tr>
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
                <tr><td>nonposix<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Create as a non-POSIX group.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State to ensure</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of user names assigned to this group.</div><div>If an empty list is passed all users will be removed from this group.</div><div>If option is omitted assigned users will not be checked or changed.</div><div>Users that are already assigned but not passed will be removed.</div>        </td></tr>
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

    # Ensure group is present
    - ipa_group:
        name: oinstall
        gidnumber: 54321
        state: present
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure that groups sysops and appops are assigned to ops but no other group
    - ipa_group:
        name: ops
        group:
        - sysops
        - appops
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure that users linus and larry are assign to the group, but no other user
    - ipa_group:
        name: sysops
        user:
        - linus
        - larry
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure group is absent
    - ipa_group:
        name: sysops
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
        <td> group </td>
        <td> Group as returned by IPA API </td>
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
