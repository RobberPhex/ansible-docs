.. _virt:


virt - Manages virtual machines supported by libvirt
++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages virtual machines supported by *libvirt*.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * libvirt-python


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
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>create</li><li>status</li><li>start</li><li>stop</li><li>pause</li><li>unpause</li><li>shutdown</li><li>undefine</li><li>destroy</li><li>get_xml</li><li>autostart</li><li>freemem</li><li>list_vms</li><li>info</li><li>nodeinfo</li><li>virttype</li><li>define</li></ul></td>
        <td><div>in addition to state management, various non-idempotent commands are available. See examples</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the guest VM being managed. Note that VM must be previously defined with xml.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>running</li><li>shutdown</li><li>destroyed</li><li>paused</li></ul></td>
        <td><div>Note that there may be some lag for state requests like <code>shutdown</code> since these refer only to VM states. After starting a guest, it may not be immediately accessible.</div></td></tr>
            <tr>
    <td>uri<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>libvirt connection uri</div></td></tr>
            <tr>
    <td>xml<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>XML document used with the define command</div></td></tr>
        </table>
    </br>



Examples
--------

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

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> status </td>
        <td> The status of the VM, among running, crashed, paused and shutdown </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> success </td>
    </tr>
            <tr>
        <td> list_vms </td>
        <td> The list of vms defined on the remote system </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center> ['build.example.org', 'dev.example.org'] </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

        
        </table>
    </td></tr>

        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

