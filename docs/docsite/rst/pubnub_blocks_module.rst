.. _pubnub_blocks:


pubnub_blocks - PubNub blocks management module.
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows Ansible to interface with the PubNub BLOCKS infrastructure by providing the following operations: create / remove, start / stop and rename for blocks and create / modify / remove for event handlers


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * pubnub_blocks_client >= 1.0


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
                <tr><td>application<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of target PubNub application for which blocks configuration on specific <code>keyset</code> will be done.</div>        </td></tr>
                <tr><td>cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>In case if single play use blocks management module few times it is preferred to enabled 'caching' by making previous module to share gathered artifacts and pass them to this parameter.
    </div>        </td></tr>
                <tr><td>changes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of fields which should be changed by block itself (doesn't affect any event handlers).</div><div>Possible options for change is: <code>name</code>.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>New block</td>
        <td></td>
        <td><div>Short block description which will be later visible on admin.pubnub.com. Used only if block doesn't exists and won't change description for existing block.</div>        </td></tr>
                <tr><td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Email from account for which new session should be started.</div><div>Not required if <code>cache</code> contains result of previous module call (in same play).</div>        </td></tr>
                <tr><td>event_handlers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of event handlers which should be updated for specified block <code>name</code>.</div><div>Each entry for new event handler should contain: <code>name</code>, <code>src</code>, <code>channels</code>, <code>event</code>. <code>name</code> used as event handler name which can be used later to make changes to it.</div><div><code>src</code> is full path to file with event handler code.</div><div><code>channels</code> is name of channel from which event handler is waiting for events.</div><div><code>event</code> is type of event which is able to trigger event handler: <em>js-before-publish</em>, <em>js-after-publish</em>, <em>js-after-presence</em>.</div><div>Each entry for existing handlers should contain <code>name</code> (so target handler can be identified). Rest parameters (<code>src</code>, <code>channels</code> and <code>event</code>) can be added if changes required for them.</div><div>It is possible to rename event handler by adding <code>changes</code> key to event handler payload and pass dictionary, which will contain single key <code>name</code>, where new name should be passed.</div><div>To remove particular event handler it is possible to set <code>state</code> for it to <code>absent</code> and it will be removed.</div>        </td></tr>
                <tr><td>keyset<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of application's keys set which is bound to managed blocks.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of managed block which will be later visible on admin.pubnub.com.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password which match to account to which specified <code>email</code> belong.</div><div>Not required if <code>cache</code> contains result of previous module call (in same play).</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>started</li><li>stopped</li><li>present</li><li>absent</li></ul></td>
        <td><div>Intended block state after event handlers creation / update process will be completed.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>This key allow to try skip certificates check when performing REST API calls. Sometimes host may have issues with certificates on it and this will cause problems to call PubNub REST API.</div><div>If check should be ignored <code>False</code> should be passed to this parameter.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Event handler create example.
    - name: Create single event handler
      pubnub_blocks:
        email: '{{ email }}'
        password: '{{ password }}'
        application: '{{ app_name }}'
        keyset: '{{ keyset_name }}'
        name: '{{ block_name }}'
        event_handlers:
          -
            src: '{{ path_to_handler_source }}'
            name: '{{ handler_name }}'
            event: 'js-before-publish'
            channels: '{{ handler_channel }}'
    
    # Change event handler trigger event type.
    - name: Change event handler 'event'
      pubnub_blocks:
        email: '{{ email }}'
        password: '{{ password }}'
        application: '{{ app_name }}'
        keyset: '{{ keyset_name }}'
        name: '{{ block_name }}'
        event_handlers:
          -
            name: '{{ handler_name }}'
            event: 'js-after-publish'
    
    # Stop block and event handlers.
    - name: Stopping block
      pubnub_blocks:
        email: '{{ email }}'
        password: '{{ password }}'
        application: '{{ app_name }}'
        keyset: '{{ keyset_name }}'
        name: '{{ block_name }}'
        state: stop
    
    # Multiple module calls with cached result passing
    - name: Create '{{ block_name }}' block
      register: module_cache
      pubnub_blocks:
        email: '{{ email }}'
        password: '{{ password }}'
        application: '{{ app_name }}'
        keyset: '{{ keyset_name }}'
        name: '{{ block_name }}'
        state: present
    - name: Add '{{ event_handler_1_name }}' handler to '{{ block_name }}'
      register: module_cache
      pubnub_blocks:
        cache: '{{ module_cache }}'
        application: '{{ app_name }}'
        keyset: '{{ keyset_name }}'
        name: '{{ block_name }}'
        state: present
        event_handlers:
          -
            src: '{{ path_to_handler_1_source }}'
            name: '{{ event_handler_1_name }}'
            channels: '{{ event_handler_1_channel }}'
            event: 'js-before-publish'
    - name: Add '{{ event_handler_2_name }}' handler to '{{ block_name }}'
      register: module_cache
      pubnub_blocks:
        cache: '{{ module_cache }}'
        application: '{{ app_name }}'
        keyset: '{{ keyset_name }}'
        name: '{{ block_name }}'
        state: present
        event_handlers:
          -
            src: '{{ path_to_handler_2_source }}'
            name: '{{ event_handler_2_name }}'
            channels: '{{ event_handler_2_channel }}'
            event: 'js-before-publish'
    - name: Start '{{ block_name }}' block
      register: module_cache
      pubnub_blocks:
        cache: '{{ module_cache }}'
        application: '{{ app_name }}'
        keyset: '{{ keyset_name }}'
        name: '{{ block_name }}'
        state: started

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
        <td> module_cache </td>
        <td> Cached account information. In case if with single play module used few times it is better to pass cached data to next module calls to speed up process. </td>
        <td align=center>  </td>
        <td align=center> dict </td>
        <td align=center>  </td>
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
