.. _gluster_volume:


gluster_volume - Manage GlusterFS volumes
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

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
    <td>bricks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Brick paths on servers. Multiple brick paths can be separated by commas</div></br>
        <div style="font-size: small;">aliases: brick<div></td></tr>
            <tr>
    <td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of hosts to use for probing and brick setup</div></td></tr>
            <tr>
    <td>directory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Directory for limit-usage</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If brick is being created in the root partition, module will fail. Set force to true to override this behaviour</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Override local hostname (for peer probing purposes)</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The volume name</div></td></tr>
            <tr>
    <td>options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary/hash with options/settings for the volume</div></td></tr>
            <tr>
    <td>quota<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Quota value for limit-usage (be sure to use 10.0MB instead of 10MB, see quota list)</div></td></tr>
            <tr>
    <td>rebalance<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Controls whether the cluster is rebalanced after changes</div></td></tr>
            <tr>
    <td>replicas<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Replica count for volume</div></td></tr>
            <tr>
    <td>start_on_create<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Controls whether the volume is started after creation or not, defaults to yes</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>started</li><li>stopped</li></ul></td>
        <td><div>Use present/absent ensure if a volume exists or not, use started/stopped to control it's availability.</div></td></tr>
            <tr>
    <td>stripes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Stripe count for volume</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>rdma</li><li>tcp,rdma</li></ul></td>
        <td><div>Transport type for volume</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create gluster volume
      gluster_volume: state=present name=test1 bricks=/bricks/brick1/g1 rebalance=yes cluster="192.168.1.10,192.168.1.11"
      run_once: true
    
    - name: tune
      gluster_volume: state=present name=test1 options='{performance.cache-size: 256MB}'
    
    - name: start gluster volume
      gluster_volume: state=started name=test1
    
    - name: limit usage
      gluster_volume: state=present name=test1 directory=/foo quota=20.0MB
    
    - name: stop gluster volume
      gluster_volume: state=stopped name=test1
    
    - name: remove gluster volume
      gluster_volume: state=absent name=test1
    
    - name: create gluster volume with multiple bricks
      gluster_volume: state=present name=test2 bricks="/bricks/brick1/g2,/bricks/brick2/g2" cluster="192.168.1.10,192.168.1.11"
      run_once: true


Notes
-----

.. note:: Requires cli tools for GlusterFS on servers
.. note:: Will add new bricks, but not remove them


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

