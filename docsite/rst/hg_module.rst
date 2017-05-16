.. _hg:


hg - Manages Mercurial (hg) repositories.
+++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.0

Manages Mercurial (hg) repositories. Supports SSH, HTTP/S and local address.

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
        <td>Absolute path of where the repository should be cloned to.</td>
    </tr>
            <tr>
    <td>executable</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path to hg executable to use. If not supplied, the normal mechanism for resolving binary paths will be used. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Discards uncommitted changes. Runs <code>hg update -C</code>.  Prior to 1.9, the default was `yes`.</td>
    </tr>
            <tr>
    <td>purge</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Deletes untracked files. Runs <code>hg purge</code>.</td>
    </tr>
            <tr>
    <td>repo</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The repository address.</td>
    </tr>
            <tr>
    <td>revision</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Equivalent <code>-r</code> option in hg command which could be the changeset, revision number, branch name or even tag.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Ensure the current working copy is inside the stable branch and deletes untracked files if any.
    - hg: repo=https://bitbucket.org/user/repo1 dest=/home/user/repo1 revision=stable purge=yes

.. note:: If the task seems to be hanging, first verify remote host is in ``known_hosts``. SSH will prompt user to authorize the first contact with a remote host.  To avoid this prompt, one solution is to add the remote host public key in ``/etc/ssh/ssh_known_hosts`` before calling the hg module, with the following command: ssh-keyscan remote_host.com >> /etc/ssh/ssh_known_hosts.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

