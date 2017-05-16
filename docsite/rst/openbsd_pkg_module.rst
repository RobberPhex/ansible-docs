.. _openbsd_pkg:


openbsd_pkg - Manage packages on OpenBSD.
+++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

Manage packages on OpenBSD using the pkg tools.

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
        <td>Name of the package.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><code>present</code> will make sure the package is installed. <code>latest</code> will make sure the latest version of the package is installed. <code>absent</code> will make sure the specified package is not installed.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Make sure nmap is installed
    - openbsd_pkg: name=nmap state=present
    
    # Make sure nmap is the latest version
    - openbsd_pkg: name=nmap state=latest
    
    # Make sure nmap is not installed
    - openbsd_pkg: name=nmap state=absent
    
    # Specify a pkg flavour with '--'
    - openbsd_pkg: name=vim--nox11 state=present
    
    # Specify the default flavour to avoid ambiguity errors
    - openbsd_pkg: name=vim-- state=present
    
    # Update all packages on the system
    - openbsd_pkg: name=* state=latest



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

