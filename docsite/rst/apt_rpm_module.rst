.. _apt_rpm:


apt_rpm - apt_rpm package manager
+++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

Manages packages with *apt-rpm*. Both low-level (*rpm*) and high-level (*apt-get*) package manager binaries required.

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
    <td>pkg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of package to install, upgrade or remove.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td>Indicates the desired package state</td>
    </tr>
            <tr>
    <td>update_cache</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>update the package database first <code>apt-get update</code>.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # install package foo
    - apt_rpm: pkg=foo state=present
    # remove package foo
    - apt_rpm: pkg=foo state=absent
    # description: remove packages foo and bar 
    - apt_rpm: pkg=foo,bar state=absent
    # description: update the package database and install bar (bar will be the updated if a newer version exists) 
    - apt_rpm: name=bar state=present update_cache=yes     



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

