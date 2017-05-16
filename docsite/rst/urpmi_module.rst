.. _urpmi:


urpmi - Urpmi manager
+++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3.4

Manages packages with *urpmi* (such as for Mageia or Mandriva)

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
    <td>force</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Corresponds to the <code>--force</code> option for <em>urpmi</em>.</td>
    </tr>
            <tr>
    <td>no-suggests</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Corresponds to the <code>--no-suggests</code> option for <em>urpmi</em>.</td>
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
        <td>update the package database first <code>urpmi.update -a</code>.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # install package foo
    - urpmi: pkg=foo state=present
    # remove package foo
    - urpmi: pkg=foo state=absent
    # description: remove packages foo and bar 
    - urpmi: pkg=foo,bar state=absent
    # description: update the package database (urpmi.update -a -q) and install bar (bar will be the updated if a newer version exists) 
    - urpmi: name=bar, state=present, update_cache=yes     



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

