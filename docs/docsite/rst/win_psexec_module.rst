.. _win_psexec:


win_psexec - Runs commands (remotely) as another (privileged) user
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Run commands (remotely) through the PsExec service
* Run commands as another (domain) user (with elevated privileges)


Requirements (on host that executes module)
-------------------------------------------

  * psexec


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
                <tr><td>chdir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Run the command from this (remote) directory.</div>        </td></tr>
                <tr><td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The command line to run through PsExec (limited to 260 characters).</div>        </td></tr>
                <tr><td>elevated<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Run the command with elevated privileges.</div>        </td></tr>
                <tr><td>executable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>psexec.exe</td>
        <td></td>
        <td><div>The location of the PsExec utility (in case it is not located in your PATH).</div>        </td></tr>
                <tr><td>hostnames<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The hostnames to run the command.</div><div>If not provided, the command is run locally.</div>        </td></tr>
                <tr><td>interactive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Run the program so that it interacts with the desktop on the remote system.</div>        </td></tr>
                <tr><td>limited<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Run the command as limited user (strips the Administrators group and allows only privileges assigned to the Users group).</div>        </td></tr>
                <tr><td>noprofile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Run the command without loading the account's profile.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password for the (remote) user to run the command as.</div><div>This is mandatory in order authenticate yourself.</div>        </td></tr>
                <tr><td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>background</li><li>low</li><li>belownormal</li><li>abovenormal</li><li>high</li><li>realtime</li></ul></td>
        <td><div>Used to run the command at a different priority.</div>        </td></tr>
                <tr><td>system<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Run the remote command in the System account.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The connection timeout in seconds</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The (remote) user to run the command as.</div><div>If not provided, the current user is used.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Wait for the application to terminate.</div><div>Only use for non-interactive applications.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Test the PsExec connection to the local system (target node) with your user
    - win_psexec:
        command: whoami.exe
    
    # Run regedit.exe locally (on target node) as SYSTEM and interactively
    - win_psexec:
        command: regedit.exe
        interactive: yes
        system: yes
    
    # Run the setup.exe installer on multiple servers using the Domain Administrator
    - win_psexec:
        command: E:\setup.exe /i /IACCEPTEULA
        hostnames:
        - remote_server1
        - remote_server2
        username: DOMAIN\Administrator
        password: some_password
        priority: high
    
    # Run PsExec from custom location C:\Program Files\sysinternals\
    - win_psexec:
        command: netsh advfirewall set allprofiles state off
        executable: C:\Program Files\sysinternals\psexec.exe
        hostnames: [ remote_server ]
        password: some_password
        priority: low

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
        <td> cmd </td>
        <td> The complete command line used by the module, including PsExec call and additional options. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> psexec.exe \\remote_server -u DOMAIN\Administrator -p some_password E:\setup.exe </td>
    </tr>
            <tr>
        <td> stderr </td>
        <td> The error output from the command </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> Error 15 running E:\setup.exe </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The standard output from the command </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> Success. </td>
    </tr>
            <tr>
        <td> msg </td>
        <td> Possible error message on failure </td>
        <td align=center> failed </td>
        <td align=center> string </td>
        <td align=center> The 'password' parameter is a required parameter. </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> Whether or not any changes were made. </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> rc </td>
        <td> The return code for the command </td>
        <td align=center> always </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
