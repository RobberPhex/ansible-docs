.. _riak:


riak - This module handles some common Riak operations
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

This module can be used to join nodes to a cluster, check the status of the cluster.

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
    <td>command</td>
    <td>no</td>
    <td></td>
        <td><ul><li>ping</li><li>kv_test</li><li>join</li><li>plan</li><li>commit</li></ul></td>
        <td>The command you would like to perform against the cluster.</td>
    </tr>
            <tr>
    <td>config_dir</td>
    <td>no</td>
    <td>/etc/riak</td>
        <td><ul></ul></td>
        <td>The path to the riak configuration directory</td>
    </tr>
            <tr>
    <td>http_conn</td>
    <td>no</td>
    <td>127.0.0.1:8098</td>
        <td><ul></ul></td>
        <td>The ip address and port that is listening for Riak HTTP queries</td>
    </tr>
            <tr>
    <td>target_node</td>
    <td>no</td>
    <td>riak@127.0.0.1</td>
        <td><ul></ul></td>
        <td>The target node for certain operations (join, ping)</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates. (added in Ansible 1.5.1)</td>
    </tr>
            <tr>
    <td>wait_for_handoffs</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Number of seconds to wait for handoffs to complete.</td>
    </tr>
            <tr>
    <td>wait_for_ring</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Number of seconds to wait for all nodes to agree on the ring.</td>
    </tr>
            <tr>
    <td>wait_for_service</td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>kv</li></ul></td>
        <td>Waits for a riak service to come online before continuing.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Join's a Riak node to another node
    - riak: command=join target_node=riak@10.1.1.1
    
    # Wait for handoffs to finish.  Use with async and poll.
    - riak: wait_for_handoffs=yes
    
    # Wait for riak_kv service to startup
    - riak: wait_for_service=kv



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

