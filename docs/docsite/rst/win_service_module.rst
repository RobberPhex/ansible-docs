.. _win_service:


win_service - Manages Windows services
++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages Windows services




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
                <tr><td>dependencies<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of service dependencies to set for this particular service.</div><div>This should be a list of service names and not the display name of the service.</div><div>This works by <code>dependency_action</code> to either add/remove or set the services in this list.</div>        </td></tr>
                <tr><td>dependency_action<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>set</td>
        <td><ul><li>set</li><li>add</li><li>remove</li></ul></td>
        <td><div>Used in conjunction with <code>dependency</code> to either add the dependencies to the existing service dependencies.</div><div>Remove the dependencies to the existing dependencies.</div><div>Set the dependencies to only the values in the list replacing the existing dependencies.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The description to set for the service.</div>        </td></tr>
                <tr><td>desktop_interact<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether to allow the service user to interact with the desktop.</div><div>This should only be set to true when using the LocalSystem username.</div>        </td></tr>
                <tr><td>display_name<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The display name to set for the service.</div>        </td></tr>
                <tr><td>force_dependent_services<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If True, stopping or restarting a service with dependent services will force the dependent services to stop or restart also.</div><div>If False, stopping or restarting a service with dependent services may fail.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the service</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password to set the service to start as.</div><div>This and the <code>username</code> argument must be supplied together.</div><div>If specifying LocalSystem, NetworkService or LocalService this field must be an empty string and not null.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to the executable to set for the service.</div>        </td></tr>
                <tr><td>start_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>auto</li><li>manual</li><li>disabled</li><li>delayed</li></ul></td>
        <td><div>Set the startup type for the service.</div><div><code>delayed</code> added in Ansible 2.3</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>absent</li></ul></td>
        <td><div><code>started</code>/<code>stopped</code>/<code>absent</code> are idempotent actions that will not run commands unless necessary.</div><div><code>restarted</code> will always bounce the service.</div><div><code>absent</code> added in Ansible 2.3</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username to set the service to start as.</div><div>This and the <code>password</code> argument must be supplied together.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Restart a service
      win_service:
        name: spooler
        state: restarted
    
    - name: Set service startup mode to auto and ensure it is started
      win_service:
        name: spooler
        start_mode: auto
        state: started
    
    # a new service will also default to the following values:
    # - username: LocalSystem
    # - state: stopped
    # - start_mode: auto
    - name: create a new service
      win_service:
        name: service name
        path: C:\temp\test.exe
    
    - name: create a new service with extra details
      win_service:
        name: service name
        path: C:\temp\test.exe
        display_name: Service Name
        description: A test service description
    
    - name: remove a service
      win_service:
        name: service name
        state: absent
    
    - name: check if a service is installed
      win_service:
        name: service name
      register: service_info
    
    - name: set the log on user to a domain account
      win_service:
        name: service name
        state: restarted
        username: DOMAIN\User
        password: Password
    
    - name: set the log on user to a local account
      win_service:
        name: service name
        state: restarted
        username: .\Administrator
        password: Password
    
    - name: set the log on user to Local System
      win_service:
        name: service name
        state: restarted
        username: LocalSystem
        password: ""
    
    - name: set the log on user to Local System and allow it to interact with the desktop
      win_service:
        name: service name
        state: restarted
        username: LocalSystem
        password: ""
        desktop_interact: True
    
    - name: set the log on user to Network Service
      win_service:
        name: service name
        state: restarted
        username: NT AUTHORITY\NetworkService
        password: ""
    
    - name: set the log on user to Local Service
      win_service:
        name: service name
        state: restarted
        username: NT AUTHORITY\LocalService
        password: ""
    
    - name: set dependencies to ones only in the list
      win_service:
        name: service name
        dependencies: ['service1', 'service2']
    
    - name: add dependencies to existing dependencies
      win_service:
        name: service name
        dependencies: ['service1', 'service2']
        dependency_action: add
    
    - name: remove dependencies from existing dependencies
      win_service:
        name: service name
        dependencies: ['service1', 'service2']
        dependency_action: remove

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
        <td> the current running status of the service </td>
        <td align=center> success and service exists </td>
        <td align=center> string </td>
        <td align=center> stopped </td>
    </tr>
            <tr>
        <td> username </td>
        <td> the username that runs the service </td>
        <td align=center> success and service exists </td>
        <td align=center> string </td>
        <td align=center> LocalSystem </td>
    </tr>
            <tr>
        <td> display_name </td>
        <td> the display name of the installed service </td>
        <td align=center> success and service exists </td>
        <td align=center> string </td>
        <td align=center> CoreMessaging </td>
    </tr>
            <tr>
        <td> name </td>
        <td> the service name or id of the service </td>
        <td align=center> success and service exists </td>
        <td align=center> string </td>
        <td align=center> CoreMessagingRegistrar </td>
    </tr>
            <tr>
        <td> exists </td>
        <td> whether the service exists or not </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> start_mode </td>
        <td> the startup type of the service </td>
        <td align=center> success and service exists </td>
        <td align=center> string </td>
        <td align=center> manual </td>
    </tr>
            <tr>
        <td> description </td>
        <td> the path to the executable of the service </td>
        <td align=center> success and service exists </td>
        <td align=center> string </td>
        <td align=center> Manages communication between system components. </td>
    </tr>
            <tr>
        <td> depended_by </td>
        <td> A list of dependencies this service relies on </td>
        <td align=center> success and service exists </td>
        <td align=center> List </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> dependencies </td>
        <td> A list of dependencies the service relies on </td>
        <td align=center> success and service exists </td>
        <td align=center> List </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> path </td>
        <td> None </td>
        <td align=center> success and service exists </td>
        <td align=center> string </td>
        <td align=center> C:\Windows\system32\svchost.exe -k LocalServiceNoNetwork </td>
    </tr>
            <tr>
        <td> desktop_interact </td>
        <td> Whether the current user is allowed to interact with the desktop </td>
        <td align=center> success and service exists </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
