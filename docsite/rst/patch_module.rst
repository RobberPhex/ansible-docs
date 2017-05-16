.. _patch:


patch - Apply patch files using the GNU patch tool.
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

Apply patch files using the GNU patch tool.

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
    <td>basedir</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path of a base directory in which the patch file will be applied. May be ommitted when <code>dest</code> option is specified, otherwise required.</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path of the file on the remote machine to be patched.The names of the files to be patched are usually taken from the patch file, but if there's just one file to be patched it can specified with this option.</td>
    </tr>
            <tr>
    <td>remote_src</td>
    <td>no</td>
    <td>False</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>If False, it will search for src at originating/master machine, if True it will go to the remote/target machine for the src. Default is False.</td>
    </tr>
            <tr>
    <td>src</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path of the patch file as accepted by the GNU patch tool. If <code>remote_src</code> is False, the patch source file is looked up from the module's "files" directory.</td>
    </tr>
            <tr>
    <td>strip</td>
    <td>no</td>
    <td>0</td>
        <td><ul></ul></td>
        <td>Number that indicates the smallest prefix containing leading slashes that will be stripped from each file name found in the patch file. For more information see the strip parameter of the GNU patch tool.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - name: apply patch to one file
      patch: >
        src=/tmp/index.html.patch
        dest=/var/www/index.html
    
    - name: apply patch to multiple files under basedir
      patch: >
        src=/tmp/customize.patch
        basedir=/var/www
        strip=1



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

