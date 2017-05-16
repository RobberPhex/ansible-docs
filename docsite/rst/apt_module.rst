.. _apt:


apt - Manages apt-packages
++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Manages *apt* packages (such as for Debian/Ubuntu).

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
    <td>cache_valid_time</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If <code>update_cache</code> is specified and the last run is less or equal than <em>cache_valid_time</em> seconds ago, the <code>update_cache</code> gets skipped.</td>
    </tr>
            <tr>
    <td>deb</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path to a .deb package on the remote machine. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>default_release</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Corresponds to the <code>-t</code> option for <em>apt</em> and sets pin priorities</td>
    </tr>
            <tr>
    <td>dpkg_options</td>
    <td>no</td>
    <td>force-confdef,force-confold</td>
        <td><ul></ul></td>
        <td>Add dpkg options to apt command. Defaults to '-o "Dpkg::Options::=--force-confdef" -o "Dpkg::Options::=--force-confold"'Options should be supplied as comma separated list</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>yes</code>, force installs/removes.</td>
    </tr>
            <tr>
    <td>install_recommends</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Corresponds to the <code>--no-install-recommends</code> option for <em>apt</em>. Default behavior (<code>yes</code>) replicates apt's default behavior; <code>no</code> does not install recommended packages. Suggested packages are never installed.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A package name, like <code>foo</code>, or package specifier with version, like <code>foo=1.0</code>. Name wildcards (fnmatch) like <code>apt*</code> and version wildcards like <code>foo=1.0*</code> are also supported.</td>
    </tr>
            <tr>
    <td>purge</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Will force purging of configuration files if the module state is set to <em>absent</em>.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>latest</li><li>absent</li><li>present</li></ul></td>
        <td>Indicates the desired package state. <code>latest</code> ensures that the latest version is installed.</td>
    </tr>
            <tr>
    <td>update_cache</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Run the equivalent of <code>apt-get update</code> before the operation. Can be run as part of the package installation or as a separate step.</td>
    </tr>
            <tr>
    <td>upgrade</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>safe</li><li>full</li><li>dist</li></ul></td>
        <td>If yes or safe, performs an aptitude safe-upgrade.If full, performs an aptitude full-upgrade.If dist, performs an apt-get dist-upgrade.Note: This does not upgrade a specific package, use state=latest for that. (added in Ansible 1.1)</td>
    </tr>
        </table>


.. note:: Requires python-apt


.. note:: Requires aptitude


Examples
--------

.. raw:: html

    <br/>


::

    # Update repositories cache and install "foo" package
    - apt: name=foo update_cache=yes
    
    # Remove "foo" package
    - apt: name=foo state=absent
    
    # Install the package "foo"
    - apt: name=foo state=present
    
    # Install the version '1.00' of package "foo"
    - apt: name=foo=1.00 state=present
    
    # Update the repository cache and update package "nginx" to latest version using default release squeeze-backport
    - apt: name=nginx state=latest default_release=squeeze-backports update_cache=yes
    
    # Install latest version of "openjdk-6-jdk" ignoring "install-recommends"
    - apt: name=openjdk-6-jdk state=latest install_recommends=no
    
    # Update all packages to the latest version
    - apt: upgrade=dist
    
    # Run the equivalent of "apt-get update" as a separate step
    - apt: update_cache=yes
    
    # Only run "update_cache=yes" if the last one is more than 3600 seconds ago
    - apt: update_cache=yes cache_valid_time=3600
    
    # Pass options to dpkg on run
    - apt: upgrade=dist update_cache=yes dpkg_options='force-confold,force-confdef'
    
    # Install a .deb package
    - apt: deb=/tmp/mypackage.deb

.. note:: Three of the upgrade modes (``full``, ``safe`` and its alias ``yes``) require ``aptitude``, otherwise ``apt-get`` suffices.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

