.. _portinstall:


portinstall - Installing packages from FreeBSD's ports system
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage packages for FreeBSD using 'portinstall'.




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
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of package to install/remove</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>state of the package</div></td></tr>
            <tr>
    <td>use_packages<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>use packages instead of ports whenever available</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install package foo
    - portinstall: name=foo state=present
    
    # Install package security/cyrus-sasl2-saslauthd
    - portinstall: name=security/cyrus-sasl2-saslauthd state=present
    
    # Remove packages foo and bar
    - portinstall: name=foo,bar state=absent




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

