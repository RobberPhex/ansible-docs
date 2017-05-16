.. _rabbitmq_policy:


rabbitmq_policy - Manage the state of policies in RabbitMQ.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

Manage the state of a virtual host in RabbitMQ.

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
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the policy to manage.</td>
    </tr>
            <tr>
    <td>node</td>
    <td>no</td>
    <td>rabbit</td>
        <td><ul></ul></td>
        <td>Erlang node name of the rabbit we wish to configure.</td>
    </tr>
            <tr>
    <td>pattern</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>A regex of queues to apply the policy to.</td>
    </tr>
            <tr>
    <td>priority</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The priority of the policy.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>The state of the policy.</td>
    </tr>
            <tr>
    <td>tags</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>A dict or string describing the policy.</td>
    </tr>
            <tr>
    <td>vhost</td>
    <td>no</td>
    <td>/</td>
        <td><ul></ul></td>
        <td>The name of the vhost to apply to.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - name: ensure the default vhost contains the HA policy via a dict
      rabbitmq_policy: name=HA pattern='.*'
      args:
        tags:
          "ha-mode": all
    
    - name: ensure the default vhost contains the HA policy
      rabbitmq_policy: name=HA pattern='.*' tags="ha-mode=all"



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

