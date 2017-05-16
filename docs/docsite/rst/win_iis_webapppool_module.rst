.. _win_iis_webapppool:


win_iis_webapppool - Configures an IIS Web Application Pool.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates, Removes and configures an IIS Web Application Pool




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
                <tr><td>attributes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Application Pool attributes from string where attributes are separated by a pipe and attribute name/values by colon Ex. "foo:1|bar:2".</div><div>The following attributes may only have the following names.</div><div>managedPipelineMode may be either "Integrated" or  "Classic".</div><div>startMode may be either "OnDemand" or  "AlwaysRunning".</div><div>state may be one of "Starting", "Started", "Stopping", "Stopped", "Unknown". Use the <code>state</code> module parameter to modify, states shown are reflect the possible runtime values.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of application pool</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>absent</li><li>stopped</li><li>started</li><li>restarted</li></ul></td>
        <td><div>State of the binding</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: return information about an existing application pool
      win_iis_webapppool:
        name: DefaultAppPool
    
    - name: Create a new application pool in 'Started' state
      win_iis_webapppool:
        name: AppPool
        state: started
    
    - name: Stop an application pool
      win_iis_webapppool:
        name: AppPool
        state: stopped
    
    - name: Restart an application pool
      win_iis_webapppool:
        name: AppPool
        state: restart
    
    - name: Changes application pool attributes without touching state
      win_iis_webapppool:
        name: AppPool
        attributes: 'managedRuntimeVersion:v4.0|autoStart:false'
    
    - name: Creates an application pool and sets attributes
      win_iis_webapppool:
        name: AnotherAppPool
        state: started
        attributes: 'managedRuntimeVersion:v4.0|autoStart:false'
    
    # Playbook example
    ---
    
    - name: App Pool with .NET 4.0
      win_iis_webapppool:
        name: 'AppPool'
        state: started
        attributes: managedRuntimeVersion:v4.0
      register: webapppool
    

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
        <td> info </td>
        <td> Information on current state of the Application Pool </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center> None </td>
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

                <tr>
        <td> attributes </td>
        <td> key value pairs showing the current Application Pool attributes </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center> {'managedRuntimeLoader': 'webengine4.dll', 'applicationPoolSid': 'S-1-5-82-1352790163-598702362-1775843902-1923651883-1762956711', 'managedPipelineMode': 'Classic', 'enable32BitAppOnWin64': True, 'name': 'DefaultAppPool', 'passAnonymousToken': True, 'CLRConfigFile': '', 'queueLength': 1000, 'state': 'Started', 'enableConfigurationOverride': True, 'autoStart': True, 'startMode': 'OnDemand', 'managedRuntimeVersion': 'v4.0'} </td>
        </tr>
                <tr>
        <td> state </td>
        <td> ['Current runtime state of the pool as the module completed.'] </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Started </td>
        </tr>
                <tr>
        <td> name </td>
        <td> ['Name of Application Pool that was processed by this module invocation.'] </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> DefaultAppPool </td>
        </tr>
        
        </table>
    </td></tr>

            <tr>
        <td> attributes </td>
        <td> ['Application Pool attributes from that were processed by this module invocation.'] </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center> {'managedPipelineMode': 'Classic', 'enable32BitAppOnWin64': 'true', 'managedRuntimeVersion': 'v4.0'} </td>
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




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
