.. _win_nssm:


win_nssm - NSSM - the Non-Sucking Service Manager
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* nssm is a service helper which doesn't suck. See https://nssm.cc/ for more information.


Requirements (on host that executes module)
-------------------------------------------

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
                <tr><td>app_parameters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Parameters to be passed to the application when it starts.</div><div>Use either this or <code>app_parameters_free_form</code>, not both</div>        </td></tr>
                <tr><td>app_parameters_free_form<br/><div style="font-size: small;"> (added in 2.3.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Single string of parameters to be passed to the service.</div><div>Use either this or <code>app_parameters</code>, not both</div>        </td></tr>
                <tr><td>application<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The application binary to run as a service</div><div>Specify this whenever the service may need to be installed (state: present, started, stopped, restarted)</div><div>Note that the application name must look like the following, if the directory includes spaces:</div><div>nssm install service "c:\\Program Files\\app.exe\\" "C:\\Path with spaces\\"</div><div>See commit 0b386fc1984ab74ee59b7bed14b7e8f57212c22b in the nssm.git project for more info: <a href='https://git.nssm.cc/?p=nssm.git;a=commit;h=0b386fc1984ab74ee59b7bed14b7e8f57212c22b'>https://git.nssm.cc/?p=nssm.git;a=commit;h=0b386fc1984ab74ee59b7bed14b7e8f57212c22b</a></div>        </td></tr>
                <tr><td>dependencies<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Service dependencies that has to be started to trigger startup, separated by comma.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the service to operate on</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password to be used for service startup</div>        </td></tr>
                <tr><td>start_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>auto</td>
        <td><ul><li>auto</li><li>manual</li><li>disabled</li></ul></td>
        <td><div>If <code>auto</code> is selected, the service will start at bootup. <code>manual</code> means that the service will start only when another service needs it. <code>disabled</code> means that the service will stay off, regardless if it is needed or not.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>present</li><li>started</li><li>stopped</li><li>restarted</li><li>absent</li></ul></td>
        <td><div>State of the service on the system</div><div>Note that NSSM actions like "pause", "continue", "rotate" do not fit the declarative style of ansible, so these should be implemented via the ansible command module</div>        </td></tr>
                <tr><td>stderr_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to receive error output</div>        </td></tr>
                <tr><td>stdout_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to receive output</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User to be used for service startup</div>        </td></tr>
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
    # This will yield the following command: C:\windows\\foo.exe -bar "true"
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        app_parameters:
          "-bar": true
    
    # Install and start the foo service with a single parameter
    # This will yield the following command: C:\windows\\foo.exe bar
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        app_parameters:
          _: bar
    
    # Install and start the foo service with a mix of single params, and key value pairs
    # This will yield the following command: C:\windows\\foo.exe bar -file output.bat
    - win_nssm:
        name: foo
        application: C:\windows\foo.exe
        app_parameters:
          _: bar
          "-file": "output.bat"
    
    # Use the single line parameters option to specify an arbitrary string of parameters
    # for the service executable
    - name: Make sure the Consul service runs
      win_nssm:
        name: consul
        application: C:\consul\consul.exe
        app_parameters_free_form: agent -config-dir=C:\consul\config
        stdout_file: C:\consul\log.txt
        stderr_file: C:\consul\error.txt
    
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





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
