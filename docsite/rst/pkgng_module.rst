.. _pkgng:


pkgng - Package manager for FreeBSD >= 9.0
++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Manage binary packages for FreeBSD using 'pkgng' which is available in versions after 9.0.

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
    <td>annotation</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a comma-separated list of keyvalue-pairs of the form &lt;+/-/:&gt;&lt;key&gt;[=&lt;value&gt;]. A '+' denotes adding an annotation, a '-' denotes removing an annotation, and ':' denotes modifying an annotation. If setting or modifying annotations, a value must be provided. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>cached</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>use local package base or try to fetch an updated one</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of package to install/remove</td>
    </tr>
            <tr>
    <td>pkgsite</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>for pkgng versions before 1.1.4, specify packagesite to use for downloading packages, if not specified, use settings from /usr/local/etc/pkg.conf for newer pkgng versions, specify a the name of a repository configured in /usr/local/etc/pkg/repos</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>state of the package</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Install package foo
    - pkgng: name=foo state=present
    
    # Annotate package foo and bar
    - pkgng: name=foo,bar annotation=+test1=baz,-test2,:test3=foobar
    
    # Remove packages foo and bar 
    - pkgng: name=foo,bar state=absent

.. note:: When using pkgsite, be careful that already in cache packages won't be downloaded again.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

