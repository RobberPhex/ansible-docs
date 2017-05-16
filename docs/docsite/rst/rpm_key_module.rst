.. _rpm_key:


rpm_key - Adds or removes a gpg key from the rpm db
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Adds or removes (rpm --import) a gpg key to your rpm database.




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
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Key that will be modified. Can be a url, a file, or a keyid if the key already exists in the database.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>If the key will be imported or removed from the rpm db.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code> and the <code>key</code> is a url starting with https, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example action to import a key from a url
    - rpm_key:
        state: present
        key: http://apt.sw.be/RPM-GPG-KEY.dag.txt
    
    # Example action to import a key from a file
    - rpm_key:
        state: present
        key: /path/to/key.gpg
    
    # Example action to ensure a key is not present in the db
    - rpm_key:
        state: absent
        key: DEADB33F





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
