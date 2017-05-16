.. _apk:


apk - Manages apk packages
++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages *apk* packages for Alpine Linux.




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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A package name, like <code>foo</code>, or mutliple packages, like <code>foo, bar</code>.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>Indicates the desired package(s) state.</div><div><code>present</code> ensures the package(s) is/are present.</div><div><code>absent</code> ensures the package(s) is/are absent.</div><div><code>latest</code> ensures the package(s) is/are present and the latest version(s).</div>        </td></tr>
                <tr><td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Update repository indexes. Can be run with other steps or on it's own.</div>        </td></tr>
                <tr><td>upgrade<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Upgrade all installed packages to their latest version.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Update repositories and install "foo" package
    - apk:
        name: foo
        update_cache: yes
    
    # Update repositories and install "foo" and "bar" packages
    - apk:
        name: foo,bar
        update_cache: yes
    
    # Remove "foo" package
    - apk:
        name: foo
        state: absent
    
    # Remove "foo" and "bar" packages
    - apk:
        name: foo,bar
        state: absent
    
    # Install the package "foo"
    - apk:
        name: foo
        state: present
    
    # Install the packages "foo" and "bar"
    - apk:
        name: foo,bar
        state: present
    
    # Update repositories and update package "foo" to latest version
    - apk:
        name: foo
        state: latest
        update_cache: yes
    
    # Update repositories and update packages "foo" and "bar" to latest versions
    - apk:
        name: foo,bar
        state: latest
        update_cache: yes
    
    # Update all installed packages to the latest versions
    - apk:
        upgrade: yes
    
    # Update repositories as a separate step
    - apk:
        update_cache: yes


Notes
-----

.. note::
    - "name" and "upgrade" are mutually exclusive.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
