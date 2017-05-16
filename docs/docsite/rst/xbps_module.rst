.. _xbps:


xbps - Manage packages with XBPS
++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage packages with the XBPS package manager.




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
        <td><div>Name of the package to install, upgrade, or remove.</div>        </td></tr>
                <tr><td>recurse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When removing a package, also remove its dependencies, provided that they are not required by other packages and were not explicitly installed by a user.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>Desired state of the package.</div>        </td></tr>
                <tr><td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to refresh the master package lists. This can be run as part of a package installation or as a separate step.</div>        </td></tr>
                <tr><td>upgrade<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to upgrade whole system</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install package foo
    - xbps: name=foo state=present
    # Upgrade package foo
    - xbps: name=foo state=latest update_cache=yes
    # Remove packages foo and bar
    - xbps: name=foo,bar state=absent
    # Recursively remove package foo
    - xbps: name=foo state=absent recurse=yes
    # Update package cache
    - xbps: update_cache=yes
    # Upgrade packages
    - xbps: upgrade=yes

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
        <td> msg </td>
        <td> Message about results </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> System Upgraded </td>
    </tr>
            <tr>
        <td> packages </td>
        <td> Packages that are affected/would be affected </td>
        <td align=center>  </td>
        <td align=center> list </td>
        <td align=center> ['ansible'] </td>
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
