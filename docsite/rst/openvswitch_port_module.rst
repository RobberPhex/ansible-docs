.. _openvswitch_port:


openvswitch_port - Manage Open vSwitch ports
++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Manage Open vSwitch ports

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
    <td>bridge</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of bridge to manage</td>
    </tr>
            <tr>
    <td>port</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of port to manage on the bridge</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether the port should exist</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td>How long to wait for ovs-vswitchd to respond</td>
    </tr>
        </table>


.. note:: Requires ovs-vsctl


Examples
--------

.. raw:: html

    <br/>


::

    # Creates port eth2 on bridge br-ex
    - openvswitch_port: bridge=br-ex port=eth2 state=present



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

