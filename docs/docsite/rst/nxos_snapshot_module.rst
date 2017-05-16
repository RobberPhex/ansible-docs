.. _nxos_snapshot:


nxos_snapshot - Manage snapshots of the running states of selected features.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create snapshots of the running states of selected features, add new show commands for snapshot creation, delete and compare existing snapshots.




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
                <tr><td>action<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>add</li><li>compare</li><li>delete</li></ul></td>
        <td><div>Define what snapshot action the module would perform.</div>        </td></tr>
                <tr><td>compare_option<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>summary</li><li>ipv4routes</li><li>ipv6routes</li></ul></td>
        <td><div>Snapshot options to be used when <code>action=compare</code>.</div>        </td></tr>
                <tr><td>comparison_results_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the file where snapshots comparison will be store.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Snapshot description to be used when <code>action=create</code>.</div>        </td></tr>
                <tr><td>element_key1<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the tags used to distinguish among row entries, to be used when <code>action=add</code>.</div>        </td></tr>
                <tr><td>element_key2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the tags used to distinguish among row entries, to be used when <code>action=add</code>.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>nxapi</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>./</td>
        <td></td>
        <td><div>Specify the path of the file where new created snapshot or snapshots comparison will be stored, to be used when <code>action=create</code> and <code>save_snapshot_locally=true</code> or <code>action=compare</code>.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td></td>
        <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>nxapi</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).</div>        </td></tr>
                <tr><td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Convenience method that allows all <em>nxos</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div>        </td></tr>
                <tr><td>row_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the tag of each row entry of the show command's XML output, to be used when <code>action=add</code>.</div>        </td></tr>
                <tr><td>save_snapshot_locally<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Specify to locally store a new created snapshot, to be used when <code>action=create</code>.</div>        </td></tr>
                <tr><td>section<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Used to name the show command output, to be used when <code>action=add</code>.</div>        </td></tr>
                <tr><td>show_command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a new show command, to be used when <code>action=add</code>.</div>        </td></tr>
                <tr><td>snapshot1<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>First snapshot to be used when <code>action=compare</code>.</div>        </td></tr>
                <tr><td>snapshot2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Second snapshot to be used when <code>action=compare</code>.</div>        </td></tr>
                <tr><td>snapshot_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Snapshot name, to be used when <code>action=create</code> or <code>action=delete</code>.</div>        </td></tr>
                <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error. NX-API can be slow to return on long-running commands (sh mac, sh bgp, etc).</div>        </td></tr>
                <tr><td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>cli</td>
        <td></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh) or nxapi.</div>        </td></tr>
                <tr><td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <code>transport=nxapi</code>, otherwise this value is ignored.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  This value is used to authenticate either the CLI login or the nxapi authentication depending on which transport is used. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.  If the transport argument is not nxapi, this value is ignored.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a snapshot and store it locally
    - nxos_snapshot:
        action: create
        snapshot_name: test_snapshot
        description: Done with Ansible
        save_snapshot_locally: true
        path: /home/user/snapshots/
        host: "{{ inventory_hostname }}"
        username: "{{ un }}"
        password: "{{ pwd }}"
    
    # Delete a snapshot
    - nxos_snapshot:
        action: delete
        snapshot_name: test_snapshot
        host: "{{ inventory_hostname }}"
        username: "{{ un }}"
        password: "{{ pwd }}"
    
    # Delete all existing snapshots
    - nxos_snapshot:
        action: delete_all
        host: "{{ inventory_hostname }}"
        username: "{{ un }}"
        password: "{{ pwd }}"
    
    # Add a show command for snapshots creation
    - nxos_snapshot:
        section: myshow
        show_command: show ip interface brief
        row_id: ROW_intf
        element_key1: intf-name
        host: "{{ inventory_hostname }}"
        username: "{{ un }}"
        password: "{{ pwd }}"
    
    # Compare two snapshots
    - nxos_snapshot:
        action: compare
        snapshot1: pre_snapshot
        snapshot2: post_snapshot
        comparison_results_file: compare_snapshots.txt
        compare_option: summary
        path: '../snapshot_reports/'
        host: "{{ inventory_hostname }}"
        username: "{{ un }}"
        password: "{{ pwd }}"

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
        <td> report_file </td>
        <td> name of the file where the new snapshot or snapshots comparison have been stored. </td>
        <td align=center> verbose mode </td>
        <td align=center> string </td>
        <td align=center> /home/gabriele/Desktop/ntc-ansible/ansible_snapshot </td>
    </tr>
            <tr>
        <td> final_snapshots </td>
        <td> list of final snapshots. </td>
        <td align=center> verbose mode </td>
        <td align=center> list </td>
        <td align=center> [{'date': 'Tue Sep 13 10:58:08 2016', 'description': 'First snapshot', 'name': 'first_snap'}, {'date': 'Tue Sep 13 10:27:31 2016', 'description': 'Pre-snapshot', 'name': 'pre_snapshot'}, {'date': 'Tue Sep 13 10:37:50 2016', 'description': 'Post-snapshot', 'name': 'post_snapshot'}] </td>
    </tr>
            <tr>
        <td> existing_snapshots </td>
        <td> list of existing snapshots. </td>
        <td align=center> verbose mode </td>
        <td align=center> list </td>
        <td align=center> [{'date': 'Tue Sep 13 10:58:08 2016', 'description': 'First snapshot', 'name': 'first_snap'}, {'date': 'Tue Sep 13 10:27:31 2016', 'description': 'Pre-snapshot', 'name': 'pre_snapshot'}] </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> commands sent to the device </td>
        <td align=center> verbose mode </td>
        <td align=center> list </td>
        <td align=center> ['snapshot create post_snapshot Post-snapshot'] </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> check to see if a change was made on the device </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - ``transport=cli`` may cause timeout errors.
    - The ``element_key1`` and ``element_key2`` parameter specify the tags used to distinguish among row entries. In most cases, only the element_key1 parameter needs to specified to be able to distinguish among row entries.
    - ``action=compare`` will always store a comparison report on a local file.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
