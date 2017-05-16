.. _pkgutil:


pkgutil - Manage CSW-Packages on Solaris
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages CSW packages (SVR4 format) on Solaris 10 and 11.
* These were the native packages on Solaris <= 10 and are available as a legacy feature in Solaris 11.
* Pkgutil is an advanced packaging system, which resolves dependency on installation. It is designed for CSW packages.




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
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Package name, e.g. (<code>CSWnrpe</code>)</div>        </td></tr>
                <tr><td>site<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the repository path to install the package from.</div><div>Its global definition is done in <code>/etc/opt/csw/pkgutil.conf</code>.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>Whether to install (<code>present</code>), or remove (<code>absent</code>) a package.</div><div>The upgrade (<code>latest</code>) operation will update/install the package to the latest version available.</div><div>Note: The module has a limitation that (<code>latest</code>) only works for one package, not lists of them.</div>        </td></tr>
                <tr><td>update_catalog<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If you want to refresh your catalog from the mirror, set this to (<code>yes</code>).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install a package
    - pkgutil:
        name: CSWcommon
        state: present
    
    # Install a package from a specific repository
    - pkgutil:
        name: CSWnrpe
        site: 'ftp://myinternal.repo/opencsw/kiel'
        state: latest





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
