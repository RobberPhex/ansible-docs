.. _homebrew:


homebrew - Package manager for Homebrew
+++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages Homebrew packages


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6


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
    <td>install_options<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>options flags to install a package</div></br>
        <div style="font-size: small;">aliases: options<div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>name of package to install/remove</div></br>
        <div style="font-size: small;">aliases: pkg, package, formula<div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/usr/local/bin</td>
        <td><ul></ul></td>
        <td><div>':' separated list of paths to search for 'brew' executable. Since A package (<em>formula</em> in homebrew parlance) location is prefixed relative to the actual path of <em>brew</em> command, providing an alternative <em>brew</em> path enables managing different set of packages in an alternative location in the system.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>head</li><li>latest</li><li>present</li><li>absent</li><li>linked</li><li>unlinked</li></ul></td>
        <td><div>state of the package</div></td></tr>
            <tr>
    <td>update_homebrew<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>update homebrew itself first</div></br>
        <div style="font-size: small;">aliases: update-brew<div></td></tr>
            <tr>
    <td>upgrade_all<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>upgrade all homebrew packages</div></br>
        <div style="font-size: small;">aliases: upgrade<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install formula foo with 'brew' in default path (C(/usr/local/bin))
    - homebrew: name=foo state=present
    
    # Install formula foo with 'brew' in alternate path C(/my/other/location/bin)
    - homebrew: name=foo path=/my/other/location/bin state=present
    
    # Update homebrew first and install formula foo with 'brew' in default path
    - homebrew: name=foo state=present update_homebrew=yes
    
    # Update homebrew first and upgrade formula foo to latest available with 'brew' in default path
    - homebrew: name=foo state=latest update_homebrew=yes
    
    # Update homebrew and upgrade all packages
    - homebrew: update_homebrew=yes upgrade_all=yes
    
    # Miscellaneous other examples
    - homebrew: name=foo state=head
    - homebrew: name=foo state=linked
    - homebrew: name=foo state=absent
    - homebrew: name=foo,bar state=absent
    - homebrew: name=foo state=present install_options=with-baz,enable-debug




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

