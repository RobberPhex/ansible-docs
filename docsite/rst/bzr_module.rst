.. _bzr:


bzr - Deploy software (or files) from bzr branches
++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

Manage *bzr* branches to deploy files or software.

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
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Absolute path of where the branch should be cloned to.</td>
    </tr>
            <tr>
    <td>executable</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path to bzr executable to use. If not supplied, the normal mechanism for resolving binary paths will be used. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>yes</code>, any modified files in the working tree will be discarded.  Before 1.9 the default value was "yes".</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>SSH or HTTP protocol address of the parent branch.</td>
    </tr>
            <tr>
    <td>version</td>
    <td>no</td>
    <td>head</td>
        <td><ul></ul></td>
        <td>What version of the branch to clone.  This can be the bzr revno or revid.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example bzr checkout from Ansible Playbooks
    - bzr: name=bzr+ssh://foosball.example.org/path/to/branch dest=/srv/checkout version=22



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

