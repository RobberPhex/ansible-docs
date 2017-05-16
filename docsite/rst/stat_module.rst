.. _stat:


stat - retrieve file or file system status
++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Retrieves facts for a file similar to the linux/unix 'stat' command.

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
    <td>follow</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether to follow symlinks</td>
    </tr>
            <tr>
    <td>get_checksum</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Whether to return a checksum of the file (currently sha1) (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>get_md5</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Whether to return the md5 sum of the file.  Will return None if we're unable to use md5 (Common for FIPS-140 compliant systems)</td>
    </tr>
            <tr>
    <td>path</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The full path of the file/object to get the facts of</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Obtain the stats of /etc/foo.conf, and check that the file still belongs
    # to 'root'. Fail otherwise.
    - stat: path=/etc/foo.conf
      register: st
    - fail: msg="Whoops! file ownership has changed"
      when: st.stat.pw_name != 'root'
    
    # Determine if a path exists and is a directory.  Note that we need to test
    # both that p.stat.isdir actually exists, and also that it's set to true.
    - stat: path=/path/to/something
      register: p
    - debug: msg="Path exists and is a directory"
      when: p.stat.isdir is defined and p.stat.isdir
    
    # Don't do md5 checksum
    - stat: path=/path/to/myhugefile get_md5=no



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

