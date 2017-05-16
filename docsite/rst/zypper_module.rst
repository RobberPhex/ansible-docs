.. _zypper:


zypper - Manage packages on SUSE and openSUSE
+++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Manage packages on SUSE and openSUSE using the zypper and rpm tools.

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
    <td>disable_gpg_check</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether to disable to GPG signature checking of the package signature being installed. Has an effect only if state is <em>present</em> or <em>latest</em>.</td>
    </tr>
            <tr>
    <td>disable_recommends</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Corresponds to the <code>--no-recommends</code> option for <em>zypper</em>. Default behavior (<code>yes</code>) modifies zypper's default behavior; <code>no</code> does install recommended packages. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>package name or package specifier wth version <code>name</code> or <code>name-1.0</code>.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><code>present</code> will make sure the package is installed. <code>latest</code>  will make sure the latest version of the package is installed. <code>absent</code>  will make sure the specified package is not installed.</td>
    </tr>
        </table>


.. note:: Requires zypper


.. note:: Requires rpm


Examples
--------

.. raw:: html

    <br/>


::

    # Install "nmap"
    - zypper: name=nmap state=present
    
    # Install apache2 with recommended packages
    - zypper: name=apache2 state=present disable_recommends=no
    
    # Remove the "nmap" package
    - zypper: name=nmap state=absent



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

