.. _svc:


svc - Manage daemontools services.
++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: None

Controls daemontools services on remote hosts using the svc utility.

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
    <td>downed</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Should a 'down' file exist or not, if it exists it disables auto startup. defaults to no. Downed does not imply stopped.</td>
    </tr>
            <tr>
    <td>enabled</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Wheater the service is enabled or not, if disabled it also implies stopped. Make note that a service can be enabled and downed (no auto restart).</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the service to manage.</td>
    </tr>
            <tr>
    <td>service_dir</td>
    <td>no</td>
    <td>/service</td>
        <td><ul></ul></td>
        <td>directory svscan watches for services</td>
    </tr>
            <tr>
    <td>service_src</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>directory where services are defined, the source of symlinks to service_dir.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>reloaded</li><li>once</li></ul></td>
        <td><code>Started</code>/<code>stopped</code> are idempotent actions that will not run commands unless necessary.  <code>restarted</code> will always bounce the svc (svc -t) and <code>killed</code> will always bounce the svc (svc -k). <code>reloaded</code> will send a sigusr1 (svc -u). <code>once</code> will run a normally downed svc once (svc -o), not really an idempotent operation.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example action to start svc dnscache, if not running
     - svc: name=dnscache state=started
    
    # Example action to stop svc dnscache, if running
     - svc: name=dnscache state=stopped
    
    # Example action to kill svc dnscache, in all cases
     - svc : name=dnscache state=killed
    
    # Example action to restart svc dnscache, in all cases
     - svc : name=dnscache state=restarted
    
    # Example action to reload svc dnscache, in all cases
     - svc: name=dnscache state=reloaded
    
    # Example using alt svc directory location
     - svc: name=dnscache state=reloaded service_dir=/var/service



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

