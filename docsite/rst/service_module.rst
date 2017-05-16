.. _service:


service - Manage services.
++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Controls services on remote hosts. Supported init systems include BSD init, OpenRC, SysV, Solaris SMF, systemd, upstart.

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
    <td>arguments</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Additional arguments provided on the command line</td>
    </tr>
            <tr>
    <td>enabled</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether the service should start on boot. <b>At least one of state and enabled are required.</b></td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the service.</td>
    </tr>
            <tr>
    <td>pattern</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If the service does not respond to the status command, name a substring to look for as would be found in the output of the <em>ps</em> command as a stand-in for a status result.  If the string is found, the service will be assumed to be running. (added in Ansible 0.7)</td>
    </tr>
            <tr>
    <td>runlevel</td>
    <td>no</td>
    <td>default</td>
        <td><ul></ul></td>
        <td>For OpenRC init scripts (ex: Gentoo) only.  The runlevel that this service belongs to.</td>
    </tr>
            <tr>
    <td>sleep</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If the service is being <code>restarted</code> then sleep this many seconds between the stop and start command. This helps to workaround badly behaving init scripts that exit immediately after signaling a process to stop. (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>reloaded</li></ul></td>
        <td><code>started</code>/<code>stopped</code> are idempotent actions that will not run commands unless necessary.  <code>restarted</code> will always bounce the service.  <code>reloaded</code> will always reload. <b>At least one of state and enabled are required.</b></td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example action to start service httpd, if not running
    - service: name=httpd state=started
    
    # Example action to stop service httpd, if running
    - service: name=httpd state=stopped
    
    # Example action to restart service httpd, in all cases
    - service: name=httpd state=restarted
    
    # Example action to reload service httpd, in all cases
    - service: name=httpd state=reloaded
    
    # Example action to enable service httpd, and not touch the running state
    - service: name=httpd enabled=yes
    
    # Example action to start service foo, based on running process /usr/bin/foo
    - service: name=foo pattern=/usr/bin/foo state=started
    
    # Example action to restart network service for interface eth0
    - service: name=network state=restarted args=eth0



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

