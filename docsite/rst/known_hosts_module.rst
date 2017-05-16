.. _known_hosts:


known_hosts - Add or remove a host from the ``known_hosts`` file
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

The ``known_hosts`` module lets you add or remove a host from the ``known_hosts`` file. This is useful if you're going to want to use the ``git`` module over ssh, for example. If you have a very large number of host keys to manage, you will find the ``template`` module more useful.

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
    <td>key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The SSH public host key, as a string (required if state=present, optional when state=absent, in which case all keys for the host are removed)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The host to add or remove (must match a host specified in key)</td>
    </tr>
            <tr>
    <td>path</td>
    <td>no</td>
    <td>(homedir)+/.ssh/known_hosts</td>
        <td><ul></ul></td>
        <td>The known_hosts file to edit</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><em>present</em> to add the host, <em>absent</em> to remove it.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example using with_file to set the system known_hosts file
    - name: tell the host about our servers it might want to ssh to
      known_hosts: path='/etc/ssh/ssh_known_hosts'
                   host='foo.com.invalid'
                   key="{{ lookup('file', 'pubkeys/foo.com.invalid') }}"



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

