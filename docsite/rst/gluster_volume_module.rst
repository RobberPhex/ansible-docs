.. _gluster_volume:


gluster_volume - Manage GlusterFS volumes
+++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

Create, remove, start, stop and tune GlusterFS volumes

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
    <td>brick</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Brick path on servers</td>
    </tr>
            <tr>
    <td>cluster</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of hosts to use for probing and brick setup</td>
    </tr>
            <tr>
    <td>directory</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Directory for limit-usage</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If brick is being created in the root partition, module will fail. Set force to true to override this behaviour</td>
    </tr>
            <tr>
    <td>host</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Override local hostname (for peer probing purposes)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The volume name</td>
    </tr>
            <tr>
    <td>options</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A dictionary/hash with options/settings for the volume</td>
    </tr>
            <tr>
    <td>quota</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Quota value for limit-usage (be sure to use 10.0MB instead of 10MB, see quota list)</td>
    </tr>
            <tr>
    <td>rebalance</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Controls whether the cluster is rebalanced after changes</td>
    </tr>
            <tr>
    <td>replicas</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Replica count for volume</td>
    </tr>
            <tr>
    <td>start_on_create</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Controls whether the volume is started after creation or not, defaults to yes</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>started</li><li>stopped</li></ul></td>
        <td>Use present/absent ensure if a volume exists or not, use started/stopped to control it's availability.</td>
    </tr>
            <tr>
    <td>stripes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Stripe count for volume</td>
    </tr>
            <tr>
    <td>transport</td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>rdma</li><li>tcp,rdma</li></ul></td>
        <td>Transport type for volume</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - name: create gluster volume
      gluster_volume: state=present name=test1 brick=/bricks/brick1/g1 rebalance=yes cluster:"{{ play_hosts }}"
      run_once: true
    
    - name: tune
      gluster_volume: state=present name=test1 options='{performance.cache-size: 256MB}'
    
    - name: start gluster volume
      gluster_volume: status=started name=test1
    
    - name: limit usage
      gluster_volume: state=present name=test1 directory=/foo quota=20.0MB
    
    - name: stop gluster volume
      gluster_volume: state=stopped name=test1
    
    - name: remove gluster volume
      gluster_volume: state=absent name=test1

.. note:: Requires cli tools for GlusterFS on servers
.. note:: Will add new bricks, but not remove them


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

