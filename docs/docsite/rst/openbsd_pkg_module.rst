.. _openbsd_pkg:


openbsd_pkg - Manage packages on OpenBSD.
+++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage packages on OpenBSD using the pkg tools.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.5


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
                <tr><td>build<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Build the package from source instead of downloading and installing a binary. Requires that the port source tree is already installed. Automatically builds and installs the 'sqlports' package, if it is not already installed.</div>        </td></tr>
                <tr><td>clean<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>When updating or removing packages, delete the extra configuration file(s) in the old packages which are annotated with @extra in the packaging-list.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the package.</div>        </td></tr>
                <tr><td>ports_dir<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>/usr/ports</td>
        <td></td>
        <td><div>When used in combination with the 'build' option, allows overriding the default ports source directory.</div>        </td></tr>
                <tr><td>quick<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Replace or delete packages quickly; do not bother with checksums before removing normal files.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><div><code>present</code> will make sure the package is installed. <code>latest</code> will make sure the latest version of the package is installed. <code>absent</code> will make sure the specified package is not installed.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Make sure nmap is installed
    - openbsd_pkg:
        name: nmap
        state: present
    
    # Make sure nmap is the latest version
    - openbsd_pkg:
        name: nmap
        state: latest
    
    # Make sure nmap is not installed
    - openbsd_pkg:
        name: nmap
        state: absent
    
    # Make sure nmap is installed, build it from source if it is not
    - openbsd_pkg:
        name: nmap
        state: present
        build: yes
    
    # Specify a pkg flavour with '--'
    - openbsd_pkg:
        name: vim--no_x11
        state: present
    
    # Specify the default flavour to avoid ambiguity errors
    - openbsd_pkg:
        name: vim--
        state: present
    
    # Specify a package branch (requires at least OpenBSD 6.0)
    - openbsd_pkg:
        name: python%3.5
        state: present
    
    # Update all packages on the system
    - openbsd_pkg:
        name: '*'
        state: latest
    
    # Purge a package and it's configuration files
    - openbsd_pkg: name=mpd clean=yes state=absent
    
    # Quickly remove a package without checking checksums
    - openbsd_pkg: name=qt5 quick=yes state=absent





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
