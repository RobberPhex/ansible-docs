.. _apt:


apt - Manages apt-packages
++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages *apt* packages (such as for Debian/Ubuntu).


Requirements (on host that executes module)
-------------------------------------------

  * python-apt (python 2)
  * python3-apt (python 3)
  * aptitude


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
                <tr><td>allow_unauthenticated<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Ignore if packages cannot be authenticated. This is useful for bootstrapping environments that manage their own apt-key setup.</div>        </td></tr>
                <tr><td>autoremove<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, remove unused dependency packages for all module states except <em>build-dep</em>. It can also be used as the only option.</div></br>
    <div style="font-size: small;">aliases: autoclean<div>        </td></tr>
                <tr><td>cache_valid_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Update the apt cache if its older than the <em>cache_valid_time</em>. This option is set in seconds.</div>        </td></tr>
                <tr><td>deb<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to a .deb package on the remote machine.</div><div>If :// in the path, ansible will attempt to download deb before installing. (Version added 2.1)</div>        </td></tr>
                <tr><td>default_release<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Corresponds to the <code>-t</code> option for <em>apt</em> and sets pin priorities</div>        </td></tr>
                <tr><td>dpkg_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>force-confdef,force-confold</td>
        <td></td>
        <td><div>Add dpkg options to apt command. Defaults to '-o "Dpkg::Options::=--force-confdef" -o "Dpkg::Options::=--force-confold"'</div><div>Options should be supplied as comma separated list</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, force installs/removes.</div>        </td></tr>
                <tr><td>install_recommends<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Corresponds to the <code>--no-install-recommends</code> option for <em>apt</em>. <code>yes</code> installs recommended packages.  <code>no</code> does not install recommended packages. By default, Ansible will use the same defaults as the operating system. Suggested packages are never installed.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A package name, like <code>foo</code>, or package specifier with version, like <code>foo=1.0</code>. Name wildcards (fnmatch) like <code>apt*</code> and version wildcards like <code>foo=1.0*</code> are also supported.  Note that the apt-get commandline supports implicit regex matches here but we do not because it can let typos through easier (If you typo <code>foo</code> as <code>fo</code> apt-get would install packages that have "fo" in their name with a warning and a prompt for the user.  Since we don't have warnings and prompts before installing we disallow this.  Use an explicit fnmatch pattern if you want wildcarding)</div></br>
    <div style="font-size: small;">aliases: pkg, package<div>        </td></tr>
                <tr><td>only_upgrade<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Only upgrade a package if it is already installed.</div>        </td></tr>
                <tr><td>purge<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Will force purging of configuration files if the module state is set to <em>absent</em>.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>latest</li><li>absent</li><li>present</li><li>build-dep</li></ul></td>
        <td><div>Indicates the desired package state. <code>latest</code> ensures that the latest version is installed. <code>build-dep</code> ensures the package build dependencies are installed.</div>        </td></tr>
                <tr><td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Run the equivalent of <code>apt-get update</code> before the operation. Can be run as part of the package installation or as a separate step.</div>        </td></tr>
                <tr><td>upgrade<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>no</li><li>yes</li><li>safe</li><li>full</li><li>dist</li></ul></td>
        <td><div>If yes or safe, performs an aptitude safe-upgrade.</div><div>If full, performs an aptitude full-upgrade.</div><div>If dist, performs an apt-get dist-upgrade.</div><div>Note: This does not upgrade a specific package, use state=latest for that.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Update repositories cache and install "foo" package
      apt:
        name: foo
        update_cache: yes
    
    - name: Remove "foo" package
      apt:
        name: foo
        state: absent
    
    - name: Install the package "foo"
      apt:
        name: foo
        state: present
    
    - name: Install the version '1.00' of package "foo"
      apt:
        name: foo=1.00
        state: present
    
    - name: Update the repository cache and update package "nginx" to latest version using default release squeeze-backport
      apt:
        name: nginx
        state: latest
        default_release: squeeze-backports
        update_cache: yes
    
    - name: Install latest version of "openjdk-6-jdk" ignoring "install-recommends"
      apt:
        name: openjdk-6-jdk
        state: latest
        install_recommends: no
    
    - name: Update all packages to the latest version
      apt:
        upgrade: dist
    
    - name: Run the equivalent of "apt-get update" as a separate step
      apt:
        update_cache: yes
    
    - name: Only run "update_cache=yes" if the last one is more than 3600 seconds ago
      apt:
        update_cache: yes
        cache_valid_time: 3600
    
    - name: Pass options to dpkg on run
      apt:
        upgrade: dist
        update_cache: yes
        dpkg_options: 'force-confold,force-confdef'
    
    - name: Install a .deb package
      apt:
        deb: /tmp/mypackage.deb
    
    - name: Install the build dependencies for package "foo"
      apt:
        pkg: foo
        state: build-dep
    
    - name: Install a .deb package from the internet.
      apt:
        deb: https://example.com/python-ppq_0.1-1_all.deb

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
        <td> cache_updated </td>
        <td> if the cache was updated or not </td>
        <td align=center> success, in some cases </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> output from apt </td>
        <td align=center> success, when needed </td>
        <td align=center> string </td>
        <td align=center> Reading package lists... Building dependency tree... Reading state information... The following extra packages will be installed: apache2-bin ... </td>
    </tr>
            <tr>
        <td> stderr </td>
        <td> error output from apt </td>
        <td align=center> success, when needed </td>
        <td align=center> string </td>
        <td align=center> AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to ... </td>
    </tr>
            <tr>
        <td> cache_update_time </td>
        <td> time of the last cache update (0 if unknown) </td>
        <td align=center> success, in some cases </td>
        <td align=center> datetime </td>
        <td align=center> 1425828348000 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Three of the upgrade modes (``full``, ``safe`` and its alias ``yes``) require ``aptitude``, otherwise ``apt-get`` suffices.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
