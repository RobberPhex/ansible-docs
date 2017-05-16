.. _virt:


virt - Manages virtual machines supported by libvirt
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Manages virtual machines supported by *libvirt*.

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
    <td>command</td>
    <td>no</td>
    <td></td>
        <td><ul><li>create</li><li>status</li><li>start</li><li>stop</li><li>pause</li><li>unpause</li><li>shutdown</li><li>undefine</li><li>destroy</li><li>get_xml</li><li>autostart</li><li>freemem</li><li>list_vms</li><li>info</li><li>nodeinfo</li><li>virttype</li><li>define</li></ul></td>
        <td>in addition to state management, various non-idempotent commands are available. See examples</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the guest VM being managed. Note that VM must be previously defined with xml.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>running</li><li>shutdown</li><li>destroyed</li><li>paused</li></ul></td>
        <td>Note that there may be some lag for state requests like <code>shutdown</code> since these refer only to VM states. After starting a guest, it may not be immediately accessible.</td>
    </tr>
            <tr>
    <td>uri</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>libvirt connection uri</td>
    </tr>
            <tr>
    <td>xml</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>XML document used with the define command</td>
    </tr>
        </table>


.. note:: Requires libvirt


Examples
--------

.. raw:: html

    <br/>


::

    # a playbook task line:
    - virt: name=alpha state=running
    
    # /usr/bin/ansible invocations
    ansible host -m virt -a "name=alpha command=status"
    ansible host -m virt -a "name=alpha command=get_xml"
    ansible host -m virt -a "name=alpha command=create uri=lxc:///"
    
    # a playbook example of defining and launching an LXC guest
    tasks:
      - name: define vm
        virt: name=foo
              command=define
              xml="{{ lookup('template', 'container-template.xml.j2') }}"
              uri=lxc:///
      - name: start vm
        virt: name=foo state=running uri=lxc:///



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

