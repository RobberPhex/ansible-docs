.. _win_nssm:


win_nssm - NSSM - the Non-Sucking Service Manager
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

nssm is a service helper which doesn't suck. See https://nssm.cc/ for more information.


Requirements
------------

  * nssm >= 2.24.0 # (install via win_chocolatey) win_chocolatey: name=nssm


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
    <td>app_parameters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Parameters to be passed to the application when it starts</div></td></tr>
            <tr>
    <td>application<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The application binary to run as a service</div><div>Specify this whenever the service may need to be installed (state: present, started, stopped, restarted)</div><div>Note that the application name must look like the following, if the directory includes spaces:</div><div>nssm install service "c:\Program Files\app.exe\" "C:\Path with spaces\"</div><div>See commit 0b386fc1984ab74ee59b7bed14b7e8f57212c22b in the nssm.git project for more info (https://git.nssm.cc/?p=nssm.git;a=commit;h=0b386fc1984ab74ee59b7bed14b7e8f57212c22b)</div></td></tr>
            <tr>
    <td>dependencies<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Service dependencies that has to be started to trigger startup, separated by comma.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the service to operate on</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password to be used for service startup</div></td></tr>
            <tr>
    <td>start_mode<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>auto</td>
        <td><ul><li>auto</li><li>manual</li><li>disabled</li></ul></td>
        <td><div>If <code>auto</code> is selected, the service will start at bootup. <code>manual</code> means that the service will start only when another service needs it. <code>disabled</code> means that the service will stay off, regardless if it is needed or not.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>present</li><li>started</li><li>stopped</li><li>restarted</li><li>absent</li></ul></td>
        <td><div>State of the service on the system</div><div>Note that NSSM actions like "pause", "continue", "rotate" do not fit the declarative style of ansible, so these should be implemented via the ansible command module</div></td></tr>
            <tr>
    <td>stderr_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to receive error output</div></td></tr>
            <tr>
    <td>stdout_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to receive output</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>User to be used for service startup</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install and start the foo service
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
    
    # Install and start the foo service with a key-value pair argument
    # This will yield the following command: C:\windows\foo.exe bar "true"
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        app_parameters:
            bar: true
    
    # Install and start the foo service with a key-value pair argument, where the argument needs to start with a dash
    # This will yield the following command: C:\windows\foo.exe -bar "true"
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        app_parameters:
            "-bar": true
    
    # Install and start the foo service with a single parameter
    # This will yield the following command: C:\windows\foo.exe bar
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        app_parameters:
            _: bar
    
    # Install and start the foo service with a mix of single params, and key value pairs
    # This will yield the following command: C:\windows\foo.exe bar -file output.bat
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        app_parameters:
            _: bar
            "-file": "output.bat"
    
    # Install and start the foo service, redirecting stdout and stderr to the same file
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        stdout_file: C:\windows\foo.log
        stderr_file: C:\windows\foo.log
    
    # Install and start the foo service, but wait for dependencies tcpip and adf
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        dependencies: 'adf,tcpip'
    
    # Install and start the foo service with dedicated user
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        user: foouser
        password: secret
    
    # Install the foo service but do not start it automatically
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        state: present
        start_mode: manual
    
    # Remove the foo service
    - win_nssm:
        name: foo
        state: absent




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

