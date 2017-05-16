.. _jenkins_plugin:


jenkins_plugin - Add or remove Jenkins plugin
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Ansible module which helps to manage Jenkins plugins.




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
                <tr><td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>jenkins</td>
        <td></td>
        <td><div>Name of the Jenkins group on the OS.</div>        </td></tr>
                <tr><td>jenkins_home<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/var/lib/jenkins</td>
        <td></td>
        <td><div>Home directory of the Jenkins user.</div>        </td></tr>
                <tr><td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0664</td>
        <td></td>
        <td><div>File mode applied on versioned plugins.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Plugin name.</div>        </td></tr>
                <tr><td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>jenkins</td>
        <td></td>
        <td><div>Name of the Jenkins user on the OS.</div>        </td></tr>
                <tr><td>params<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Option used to allow the user to overwrite any of the other options. To remove an option, set the value of the option to <code>null</code>.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li><li>pinned</li><li>unpinned</li><li>enabled</li><li>disabled</li><li>latest</li></ul></td>
        <td><div>Desired plugin state.</div><div>If the <code>latest</code> is set, the check for new version will be performed every time. This is suitable to keep the plugin up-to-date.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td></td>
        <td><div>Server connection timeout in secs.</div>        </td></tr>
                <tr><td>updates_expiration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>86400</td>
        <td></td>
        <td><div>Number of seconds after which a new copy of the <em>update-center.json</em> file is downloaded. This is used to avoid the need to download the plugin to calculate its checksum when <code>latest</code> is specified.</div><div>Set it to <code>0</code> if no cache file should be used. In that case, the plugin file will always be downloaded to calculate its checksum when <code>latest</code> is specified.</div>        </td></tr>
                <tr><td>updates_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://updates.jenkins-ci.org</td>
        <td></td>
        <td><div>URL of the Update Centre.</div><div>Used as the base URL to download the plugins and the <em>update-center.json</em> JSON file.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://localhost:8080</td>
        <td></td>
        <td><div>URL of the Jenkins server.</div>        </td></tr>
                <tr><td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Plugin version number.</div><div>If this option is specified, all plugin dependencies must be installed manually.</div><div>It might take longer to verify that the correct version is installed. This is especially true if a specific version number is specified.</div><div>Quote the version to prevent the value to be interpreted as float. For example if <code>1.20</code> would be unquoted, it would become <code>1.2</code>.</div>        </td></tr>
                <tr><td>with_dependencies<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Defines whether to install plugin dependencies.</div><div>This option takes effect only if the <em>version</em> is not defined.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Install plugin
      jenkins_plugin:
        name: build-pipeline-plugin
    
    - name: Install plugin without its dependencies
      jenkins_plugin:
        name: build-pipeline-plugin
        with_dependencies: no
    
    - name: Make sure the plugin is always up-to-date
      jenkins_plugin:
        name: token-macro
        state: latest
    
    - name: Install specific version of the plugin
      jenkins_plugin:
        name: token-macro
        version: "1.15"
    
    - name: Pin the plugin
      jenkins_plugin:
        name: token-macro
        state: pinned
    
    - name: Unpin the plugin
      jenkins_plugin:
        name: token-macro
        state: unpinned
    
    - name: Enable the plugin
      jenkins_plugin:
        name: token-macro
        state: enabled
    
    - name: Disable the plugin
      jenkins_plugin:
        name: token-macro
        state: disabled
    
    - name: Uninstall plugin
      jenkins_plugin:
        name: build-pipeline-plugin
        state: absent
    
    #
    # Example of how to use the params
    #
    # Define a variable and specify all default parameters you want to use across
    # all jenkins_plugin calls:
    #
    # my_jenkins_params:
    #   url_username: admin
    #   url_password: p4ssw0rd
    #   url: http://localhost:8888
    #
    - name: Install plugin
      jenkins_plugin:
        name: build-pipeline-plugin
        params: "{{ my_jenkins_params }}"
    
    #
    # Example of a Play which handles Jenkins restarts during the state changes
    #
    - name: Jenkins Master play
      hosts: jenkins-master
      vars:
        my_jenkins_plugins:
          token-macro:
            enabled: yes
          build-pipeline-plugin:
            version: "1.4.9"
            pinned: no
            enabled: yes
      tasks:
        - name: Install plugins without a specific version
          jenkins_plugin:
            name: "{{ item.key }}"
          register: my_jenkins_plugin_unversioned
          when: >
            'version' not in item.value
          with_dict: "{{ my_jenkins_plugins }}"
    
        - name: Install plugins with a specific version
          jenkins_plugin:
            name: "{{ item.key }}"
            version: "{{ item.value['version'] }}"
          register: my_jenkins_plugin_versioned
          when: >
            'version' in item.value
          with_dict: "{{ my_jenkins_plugins }}"
    
        - name: Initiate the fact
          set_fact:
            jenkins_restart_required: no
    
        - name: Check if restart is required by any of the versioned plugins
          set_fact:
            jenkins_restart_required: yes
          when: item.changed
          with_items: "{{ my_jenkins_plugin_versioned.results }}"
    
        - name: Check if restart is required by any of the unversioned plugins
          set_fact:
            jenkins_restart_required: yes
          when: item.changed
          with_items: "{{ my_jenkins_plugin_unversioned.results }}"
    
        - name: Restart Jenkins if required
          service:
            name: jenkins
            state: restarted
          when: jenkins_restart_required
    
        - name: Wait for Jenkins to start up
          uri:
            url: http://localhost:8080
            status_code: 200
            timeout: 5
          register: jenkins_service_status
          # Keep trying for 5 mins in 5 sec intervals
          retries: 60
          delay: 5
          until: >
             'status' in jenkins_service_status and
             jenkins_service_status['status'] == 200
          when: jenkins_restart_required
    
        - name: Reset the fact
          set_fact:
            jenkins_restart_required: no
          when: jenkins_restart_required
    
        - name: Plugin pinning
          jenkins_plugin:
            name: "{{ item.key }}"
            state: "{{ 'pinned' if item.value['pinned'] else 'unpinned'}}"
          when: >
            'pinned' in item.value
          with_dict: "{{ my_jenkins_plugins }}"
    
        - name: Plugin enabling
          jenkins_plugin:
            name: "{{ item.key }}"
            state: "{{ 'enabled' if item.value['enabled'] else 'disabled'}}"
          when: >
            'enabled' in item.value
          with_dict: "{{ my_jenkins_plugins }}"

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
        <td> state </td>
        <td> state of the target, after execution </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> plugin </td>
        <td> plugin name </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> build-pipeline-plugin </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Plugin installation should be run under root or the same user which owns the plugin files on the disk. Only if the plugin is not installed yet and no version is specified, the API installation is performed which requires only the Web UI credentials.
    - It's necessary to notify the handler or call the *service* module to restart the Jenkins service after a new plugin was installed.
    - Pinning works only if the plugin is installed and Jenkis service was successfully restarted after the plugin installation.
    - It is not possible to run the module remotely by changing the *url* parameter to point to the Jenkins server. The module must be used on the host where Jenkins runs as it needs direct access to the plugin files.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
