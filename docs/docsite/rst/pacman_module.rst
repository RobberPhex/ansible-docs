.. _pacman:


pacman - Manage packages with *pacman*
++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage packages with the *pacman* package manager, which is used by Arch Linux and its variants.




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
                <tr><td>force<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When removing package - force remove package, without any checks. When update_cache - force redownload repo databases.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the package to install, upgrade, or remove.</div></br>
    <div style="font-size: small;">aliases: pkg, package<div>        </td></tr>
                <tr><td>recurse<br/><div style="font-size: small;"> (added in 1.3)</div></td>
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
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to refresh the master package lists. This can be run as part of a package installation or as a separate step.</div></br>
    <div style="font-size: small;">aliases: update-cache<div>        </td></tr>
                <tr><td>upgrade<br/><div style="font-size: small;"> (added in 2.0)</div></td>
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
    - pacman:
        name: foo
        state: present
    
    # Upgrade package foo
    - pacman:
        name: foo
        state: latest
        update_cache: yes
    
    # Remove packages foo and bar
    - pacman:
        name: foo,bar
        state: absent
    
    # Recursively remove package baz
    - pacman:
        name: baz
        state: absent
        recurse: yes
    
    # Run the equivalent of "pacman -Sy" as a separate step
    - pacman:
        update_cache: yes
    
    # Run the equivalent of "pacman -Su" as a separate step
    - pacman:
        upgrade: yes
    
    # Run the equivalent of "pacman -Syu" as a separate step
    - pacman:
        update_cache: yes
        upgrade: yes
    
    # Run the equivalent of "pacman -Rdd", force remove package baz
    - pacman:
        name: baz
        state: absent
        force: yes

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
        <td> packages </td>
        <td> a list of packages that have been changed </td>
        <td align=center> when upgrade is set to yes </td>
        <td align=center> list of strings </td>
        <td align=center> ['package', 'other-package'] </td>
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
