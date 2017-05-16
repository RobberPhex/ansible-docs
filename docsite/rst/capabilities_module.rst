.. _capabilities:


capabilities - Manage Linux capabilities
++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

This module manipulates files privileges using the Linux capabilities(7) system.

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
    <td>capability</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Desired capability to set (with operator and flags, if state is <code>present</code>) or remove (if state is <code>absent</code>)</td>
    </tr>
            <tr>
    <td>path</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specifies the path to the file to be managed.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether the entry should be present or absent in the file's capabilities.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Set cap_sys_chroot+ep on /foo
    - capabilities: path=/foo capability=cap_sys_chroot+ep state=present
    
    # Remove cap_net_bind_service from /bar
    - capabilities: path=/bar capability=cap_net_bind_service state=absent

.. note:: The capabilities system will automatically transform operators and flags into the effective set, so (for example, cap_foo=ep will probably become cap_foo+ep). This module does not attempt to determine the final operator and flags to compare, so you will want to ensure that your capabilities argument matches the final capabilities.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

