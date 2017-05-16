.. _portage:


portage - Package manager for Gentoo
++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Manages Gentoo packages

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
    <td>changed_use</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Include installed packages where USE flags have changed, except whenflags that the user has not enabled are added or removed(--changed-use) (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>deep</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Consider the entire dependency tree of packages (--deep)</td>
    </tr>
            <tr>
    <td>depclean</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Remove packages not needed by explicitly merged packages (--depclean)If no package is specified, clean up the world's dependenciesOtherwise, --depclean serves as a dependency aware version of --unmerge</td>
    </tr>
            <tr>
    <td>newuse</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Include installed packages where USE flags have changed (--newuse)</td>
    </tr>
            <tr>
    <td>nodeps</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Only merge packages but not their dependencies (--nodeps)</td>
    </tr>
            <tr>
    <td>noreplace</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Do not re-emerge installed packages (--noreplace)</td>
    </tr>
            <tr>
    <td>oneshot</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Do not add the packages to the world file (--oneshot)</td>
    </tr>
            <tr>
    <td>onlydeps</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Only merge packages' dependencies but not the packages (--onlydeps)</td>
    </tr>
            <tr>
    <td>package</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Package atom or set, e.g. <code>sys-apps/foo</code> or <code>&gt;foo-2.13</code> or <code>@world</code></td>
    </tr>
            <tr>
    <td>quiet</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Run emerge in quiet mode (--quiet)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>installed</li><li>emerged</li><li>absent</li><li>removed</li><li>unmerged</li></ul></td>
        <td>State of the package atom</td>
    </tr>
            <tr>
    <td>sync</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>web</li></ul></td>
        <td>Sync package repositories firstIf yes, perform "emerge --sync"If web, perform "emerge-webrsync"</td>
    </tr>
            <tr>
    <td>update</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Update packages to the best version available (--update)</td>
    </tr>
            <tr>
    <td>verbose</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li></ul></td>
        <td>Run emerge in verbose mode (--verbose)</td>
    </tr>
        </table>


.. note:: Requires gentoolkit


Examples
--------

.. raw:: html

    <br/>


::

    # Make sure package foo is installed
    - portage: package=foo state=present
    
    # Make sure package foo is not installed
    - portage: package=foo state=absent
    
    # Update package foo to the "best" version
    - portage: package=foo update=yes
    
    # Sync repositories and update world
    - portage: package=@world update=yes deep=yes sync=yes
    
    # Remove unneeded packages
    - portage: depclean=yes
    
    # Remove package foo if it is not explicitly needed
    - portage: package=foo state=absent depclean=yes



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

