.. _bigpanda:


bigpanda - Notify BigPanda about deployments
++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.8

Notify BigPanda when deployments start and end (successfully or not). Returns a deployment object containing all the parameters for future module calls.

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
    <td>component</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the component being deployed. Ex: billing</td>
    </tr>
            <tr>
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Free text description of the deployment.</td>
    </tr>
            <tr>
    <td>env</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The environment name, typically 'production', 'staging', etc.</td>
    </tr>
            <tr>
    <td>hosts</td>
    <td>no</td>
    <td>machine's hostname</td>
        <td><ul></ul></td>
        <td>Name of affected host name. Can be a list.</td>
    </tr>
            <tr>
    <td>owner</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The person responsible for the deployment.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>started</li><li>finished</li><li>failed</li></ul></td>
        <td>State of the deployment.</td>
    </tr>
            <tr>
    <td>token</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>API token.</td>
    </tr>
            <tr>
    <td>url</td>
    <td>no</td>
    <td>https://api.bigpanda.io</td>
        <td><ul></ul></td>
        <td>Base URL of the API server.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates for the target url will not be validated. This should only be used on personally controlled sites using self-signed certificates.</td>
    </tr>
            <tr>
    <td>version</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The deployment version.</td>
    </tr>
        </table>


.. note:: Requires urllib


.. note:: Requires urllib2


Examples
--------

.. raw:: html

    <br/>


::

    - bigpanda: component=myapp version=1.3 token={{ bigpanda_token }} state=started
    ...
    - bigpanda: component=myapp version=1.3 token={{ bigpanda_token }} state=finished
    
    or using a deployment object:
    - bigpanda: component=myapp version=1.3 token={{ bigpanda_token }} state=started
      register: deployment
    
    - bigpanda: state=finished
      args: deployment
    
    If outside servers aren't reachable from your machine, use local_action and pass the hostname:
    - local_action: bigpanda component=myapp version=1.3 hosts={{ansible_hostname}} token={{ bigpanda_token }} state=started
      register: deployment
    ...
    - local_action: bigpanda state=finished
      args: deployment



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

