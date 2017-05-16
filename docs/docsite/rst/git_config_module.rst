.. _git_config:


git_config - Read and write git configuration
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``git_config`` module changes git configuration by invoking 'git config'. This is needed if you don't want to use :ref:`template <template>` for the entire git config file (e.g. because you need to change just ``user.email`` in /etc/.git/config).  Solutions involving :ref:`command <command>` are cumbersone or don't work correctly in check mode.


Requirements (on host that executes module)
-------------------------------------------

  * git


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
                <tr><td>list_all<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>List all settings (optionally limited to a given <em>scope</em>)</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the setting. If no value is supplied, the value will be read from the config if it has been set.</div>        </td></tr>
                <tr><td>repo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to a git repository for reading and writing values from a specific repo.</div>        </td></tr>
                <tr><td>scope<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>local</li><li>global</li><li>system</li></ul></td>
        <td><div>Specify which scope to read/set values from. This is required when setting config values. If this is set to local, you must also specify the repo parameter. It defaults to system only when not using <em>list_all</em>=yes.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When specifying the name of a single setting, supply a value to set that setting to the given value.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set some settings in ~/.gitconfig
    - git_config:
        name: alias.ci
        scope: global
        value: commit
    
    - git_config:
        name: alias.st
        scope: global
        value: status
    
    # Or system-wide:
    - git_config:
        name: alias.remotev
        scope: system
        value: remote -v
    
    - git_config:
        name: core.editor
        scope: global
        value: vim
    
    # scope=system is the default
    - git_config:
        name: alias.diffc
        value: diff --cached
    
    - git_config:
        name: color.ui
        value: auto
    
    # Make etckeeper not complain when invoked by cron
    - git_config:
        name: user.email
        repo: /etc
        scope: local
        value: 'root@{{ ansible_fqdn }}'
    
    # Read individual values from git config
    - git_config:
        name: alias.ci
        scope: global
    
    # scope: system is also assumed when reading values, unless list_all=yes
    - git_config:
        name: alias.diffc
    
    # Read all values from git config
    - git_config:
        list_all: yes
        scope: global
    
    # When list_all=yes and no scope is specified, you get configuration from all scopes
    - git_config:
        list_all: yes
    
    # Specify a repository to include local settings
    - git_config:
        list_all: yes
        repo: /path/to/repo.git

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
        <td> config_value </td>
        <td> When list_all=no and value is not set, a string containing the value of the setting in name </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> vim </td>
    </tr>
            <tr>
        <td> config_values </td>
        <td> When list_all=yes, a dict containing key/value pairs of multiple configuration settings </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center> {'core.editor': 'vim', 'color.ui': 'auto', 'alias.diffc': 'diff --cached', 'alias.remotev': 'remote -v'} </td>
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
