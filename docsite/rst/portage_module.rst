.. _portage:


portage - Package manager for Gentoo
++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages Gentoo packages


Requirements (on host that executes module)
-------------------------------------------

  * gentoolkit


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
    <td>changed_use<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td><div>Include installed packages where USE flags have changed, except when</div><div>flags that the user has not enabled are added or removed</div><div>(--changed-use)</div></td></tr>
            <tr>
    <td>deep<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td><div>Consider the entire dependency tree of packages (--deep)</div></td></tr>
            <tr>
    <td>depclean<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Remove packages not needed by explicitly merged packages (--depclean)</div><div>If no package is specified, clean up the world's dependencies</div><div>Otherwise, --depclean serves as a dependency aware version of --unmerge</div></td></tr>
            <tr>
    <td>getbinpkg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Prefer packages specified at PORTAGE_BINHOST in make.conf</div></td></tr>
            <tr>
    <td>newuse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td><div>Include installed packages where USE flags have changed (--newuse)</div></td></tr>
            <tr>
    <td>nodeps<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Only merge packages but not their dependencies (--nodeps)</div></td></tr>
            <tr>
    <td>noreplace<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Do not re-emerge installed packages (--noreplace)</div></td></tr>
            <tr>
    <td>oneshot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Do not add the packages to the world file (--oneshot)</div></td></tr>
            <tr>
    <td>onlydeps<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Only merge packages' dependencies but not the packages (--onlydeps)</div></td></tr>
            <tr>
    <td>package<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Package atom or set, e.g. <code>sys-apps/foo</code> or <code>&gt;foo-2.13</code> or <code>@world</code></div></td></tr>
            <tr>
    <td>quiet<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Run emerge in quiet mode (--quiet)</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>installed</li><li>emerged</li><li>absent</li><li>removed</li><li>unmerged</li></ul></td>
        <td><div>State of the package atom</div></td></tr>
            <tr>
    <td>sync<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>web</li><li>no</li></ul></td>
        <td><div>Sync package repositories first</div><div>If yes, perform "emerge --sync"</div><div>If web, perform "emerge-webrsync"</div></td></tr>
            <tr>
    <td>update<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td><div>Update packages to the best version available (--update)</div></td></tr>
            <tr>
    <td>usepkgonly<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Merge only binaries (no compiling). This sets getbinpkg=yes.</div></td></tr>
            <tr>
    <td>verbose<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Run emerge in verbose mode (--verbose)</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Make sure package foo is installed
    - portage: package=foo state=present
    
    # Make sure package foo is not installed
    - portage: package=foo state=absent
    
    # Update package foo to the "best" version
    - portage: package=foo update=yes
    
    # Install package foo using PORTAGE_BINHOST setup
    - portage: package=foo getbinpkg=yes
    
    # Re-install world from binary packages only and do not allow any compiling
    - portage: package=@world usepkgonly=yes
    
    # Sync repositories and update world
    - portage: package=@world update=yes deep=yes sync=yes
    
    # Remove unneeded packages
    - portage: depclean=yes
    
    # Remove package foo if it is not explicitly needed
    - portage: package=foo state=absent depclean=yes




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

