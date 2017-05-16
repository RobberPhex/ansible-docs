.. _pkgutil:


pkgutil - Manage CSW-Packages on Solaris
++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Manages CSW packages (SVR4 format) on Solaris 10 and 11.
These were the native packages on Solaris <= 10 and are available as a legacy feature in Solaris 11.
Pkgutil is an advanced packaging system, which resolves dependency on installation. It is designed for CSW packages.

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
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Package name, e.g. (<code>CSWnrpe</code>)</td>
    </tr>
            <tr>
    <td>site</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specifies the repository path to install the package from.Its global definition is done in <code>/etc/opt/csw/pkgutil.conf</code>.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td>Whether to install (<code>present</code>), or remove (<code>absent</code>) a package.The upgrade (<code>latest</code>) operation will update/install the package to the latest version available.Note: The module has a limitation that (<code>latest</code>) only works for one package, not lists of them.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Install a package
    pkgutil: name=CSWcommon state=present
    
    # Install a package from a specific repository
    pkgutil: name=CSWnrpe site='ftp://myinternal.repo/opencsw/kiel state=latest'



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

