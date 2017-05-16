.. _pkgin:


pkgin - Package manager for SmartOS, NetBSD, et al.
+++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

The standard package manager for SmartOS, but also usable on NetBSD or any OS that uses ``pkgsrc``.  (Home: http://pkgin.net/)




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
    <td>clean<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Clean packages cache</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Force package reinstall</div></td></tr>
            <tr>
    <td>full_upgrade<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Upgrade all packages to their newer versions</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of package to install/remove;</div><div>multiple names may be given, separated by commas</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Intended state of the package</div></td></tr>
            <tr>
    <td>update_cache<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Update repository database. Can be run with other steps or on it's own.</div></td></tr>
            <tr>
    <td>upgrade<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Upgrade main packages to their newer versions</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # install package foo
    - pkgin: name=foo state=present
    
    # Update database and install "foo" package
    - pkgin: name=foo update_cache=yes
    
    # remove package foo
    - pkgin: name=foo state=absent
    
    # remove packages foo and bar
    - pkgin: name=foo,bar state=absent
    
    # Update repositories as a separate step
    - pkgin: update_cache=yes
    
    # Upgrade main packages (equivalent to C(pkgin upgrade))
    - pkgin: upgrade=yes
    
    # Upgrade all packages (equivalent to C(pkgin full-upgrade))
    - pkgin: full_upgrade=yes
    
    # Force-upgrade all packages (equivalent to C(pkgin -F full-upgrade))
    - pkgin: full_upgrade=yes force=yes
    
    # clean packages cache (equivalent to C(pkgin clean))
    - pkgin: clean=yes


Notes
-----

.. note:: Known bug with pkgin < 0.8.0: if a package is removed and another package depends on it, the other package will be silently removed as well.  New to Ansible 1.9: check-mode support.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

