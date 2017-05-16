.. _win_iis_webapppool:


win_iis_webapppool - Configures a IIS Web Application Pool.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates, Removes and configures a IIS Web Application Pool




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
    <td>attributes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Application Pool attributes from string where attributes are seperated by a pipe and attribute name/values by colon Ex. "foo:1|bar:2"</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Names of application pool</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>absent</li><li>stopped</li><li>started</li><li>restarted</li></ul></td>
        <td><div>State of the binding</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # This return information about an existing application pool
    $ansible -i inventory -m win_iis_webapppool -a "name='DefaultAppPool'" windows
    host | success >> {
        "attributes": {},
        "changed": false,
        "info": {
            "attributes": {
                "CLRConfigFile": "",
                "applicationPoolSid": "S-1-5-82-3006700770-424185619-1745488364-794895919-4004696415",
                "autoStart": true,
                "enable32BitAppOnWin64": false,
                "enableConfigurationOverride": true,
                "managedPipelineMode": 0,
                "managedRuntimeLoader": "webengine4.dll",
                "managedRuntimeVersion": "v4.0",
                "name": "DefaultAppPool",
                "passAnonymousToken": true,
                "queueLength": 1000,
                "startMode": 0,
                "state": 1
            },
            "name": "DefaultAppPool",
            "state": "Started"
        }
    }
    
    # This creates a new application pool in 'Started' state
    $  ansible -i inventory -m win_iis_webapppool -a "name='AppPool' state=started" windows
    
    # This stoppes an application pool
    $  ansible -i inventory -m win_iis_webapppool -a "name='AppPool' state=stopped" windows
    
    # This restarts an application pool
    $  ansible -i inventory -m win_iis_webapppool -a "name='AppPool' state=restart" windows
    
    # This restarts an application pool
    $  ansible -i inventory -m win_iis_webapppool -a "name='AppPool' state=restart" windows
    
    # This change application pool attributes without touching state
    $  ansible -i inventory -m win_iis_webapppool -a "name='AppPool' attributes='managedRuntimeVersion:v4.0|autoStart:false'" windows
    
    # This creates an application pool and sets attributes
    $  ansible -i inventory -m win_iis_webapppool -a "name='AnotherAppPool' state=started attributes='managedRuntimeVersion:v4.0|autoStart:false'" windows
    
    
    # Playbook example
    ---
    
    - name: App Pool with .NET 4.0
      win_iis_webapppool:
        name: 'AppPool'
        state: started
        attributes: managedRuntimeVersion:v4.0
      register: webapppool
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

