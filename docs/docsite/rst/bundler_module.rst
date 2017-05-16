.. _bundler:


bundler - Manage Ruby Gem dependencies with Bundler
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage installation and Gem version dependencies for Ruby using the Bundler gem




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
                <tr><td>binstub_directory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Only applies if state is <code>present</code>. Specifies the directory to install any gem bins files to. When executed the bin files will run within the context of the Gemfile and fail if any required gem dependencies are not installed. If <code>chdir</code> is set then this path is relative to <code>chdir</code></div>        </td></tr>
                <tr><td>chdir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>temporary working directory</td>
        <td></td>
        <td><div>The directory to execute the bundler commands from. This directoy needs to contain a valid Gemfile or .bundle/ directory</div>        </td></tr>
                <tr><td>clean<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Only applies if state is <code>present</code>. If set removes any gems on the target host that are not in the gemfile</div>        </td></tr>
                <tr><td>deployment_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Only applies if state is <code>present</code>. If set it will only install gems that are in the default or production groups. Requires a Gemfile.lock file to have been created prior</div>        </td></tr>
                <tr><td>exclude_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of Gemfile groups to exclude during operations. This only applies when state is <code>present</code>. Bundler considers this a 'remembered' property for the Gemfile and will automatically exclude groups in future operations even if <code>exclude_groups</code> is not set</div>        </td></tr>
                <tr><td>executable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to the bundler executable</div>        </td></tr>
                <tr><td>extra_args<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A space separated string of additional commands that can be applied to the Bundler command. Refer to the Bundler documentation for more information</div>        </td></tr>
                <tr><td>gem_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>RubyGems gem paths</td>
        <td></td>
        <td><div>Only applies if state is <code>present</code>. Specifies the directory to install the gems into. If <code>chdir</code> is set then this path is relative to <code>chdir</code></div>        </td></tr>
                <tr><td>gemfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Gemfile in current directory</td>
        <td></td>
        <td><div>Only applies if state is <code>present</code>. The path to the gemfile to use to install gems.</div>        </td></tr>
                <tr><td>local<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If set only installs gems from the cache on the target host</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li></ul></td>
        <td><div>The desired state of the Gem bundle. <code>latest</code> updates gems to the most recent, acceptable version</div>        </td></tr>
                <tr><td>user_install<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Only applies if state is <code>present</code>. Installs gems in the local user's cache or for all users</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Installs gems from a Gemfile in the current directory
    - bundler:
        state: present
        executable: ~/.rvm/gems/2.1.5/bin/bundle
    
    # Excludes the production group from installing
    - bundler:
        state: present
        exclude_groups: production
    
    # Only install gems from the default and production groups
    - bundler:
        state: present
        deployment_mode: yes
    
    # Installs gems using a Gemfile in another directory
    - bundler:
        state: present
        gemfile: ../rails_project/Gemfile
    
    # Updates Gemfile in another directory
    - bundler:
        state: latest
        chdir: ~/rails_project





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
