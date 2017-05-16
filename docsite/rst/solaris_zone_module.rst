.. _solaris_zone:


solaris_zone - Manage Solaris zones
+++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, start, stop and delete Solaris zones. This module doesn't currently allow changing of options for a zone that's already been created.


Requirements (on host that executes module)
-------------------------------------------

  * Solaris 10 or 11


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
    <td>attach_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>empty string</td>
        <td><ul></ul></td>
        <td><div>Extra options to the zoneadm attach command. For example, this can be used to specify whether a minimum or full update of packages is required and if any packages need to be deleted. For valid values, see zoneadm(1M)</div></td></tr>
            <tr>
    <td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>empty string</td>
        <td><ul></ul></td>
        <td><div>The zonecfg configuration commands for this zone. See zonecfg(1M) for the valid options and syntax. Typically this is a list of options separated by semi-colons or new lines, e.g. "set auto-boot=true;add net;set physical=bge0;set address=10.1.1.1;end"</div></td></tr>
            <tr>
    <td>create_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>empty string</td>
        <td><ul></ul></td>
        <td><div>Extra options to the zonecfg(1M) create command.</div></td></tr>
            <tr>
    <td>install_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>empty string</td>
        <td><ul></ul></td>
        <td><div>Extra options to the zoneadm(1M) install command. To automate Solaris 11 zone creation, use this to specify the profile XML file, e.g. install_options="-c sc_profile.xml"</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Zone name.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path where the zone will be created. This is required when the zone is created, but not used otherwise.</div></td></tr>
            <tr>
    <td>root_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password hash for the root account. If not specified, the zone's root account will not have a password.</div></td></tr>
            <tr>
    <td>sparse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether to create a sparse (<code>true</code>) or whole root (<code>false</code>) zone.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>installed</li><li>started</li><li>running</li><li>stopped</li><li>absent</li><li>configured</li><li>attached</li><li>detached</li></ul></td>
        <td><div><code>present</code>, configure and install the zone.</div><div><code>installed</code>, synonym for <code>present</code>.</div><div><code>running</code>, if the zone already exists, boot it, otherwise, configure and install the zone first, then boot it.</div><div><code>started</code>, synonym for <code>running</code>.</div><div><code>stopped</code>, shutdown a zone.</div><div><code>absent</code>, destroy the zone.</div><div><code>configured</code>, configure the ready so that it's to be attached.</div><div><code>attached</code>, attach a zone, but do not boot it.</div><div><code>detached</code>, shutdown and detach a zone</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>Timeout, in seconds, for zone to boot.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create and install a zone, but don't boot it
    solaris_zone: name=zone1 state=present path=/zones/zone1 sparse=true root_password="Be9oX7OSwWoU."
          config='set autoboot=true; add net; set physical=bge0; set address=10.1.1.1; end'
    
    # Create and install a zone and boot it
    solaris_zone: name=zone1 state=running path=/zones/zone1 root_password="Be9oX7OSwWoU."
          config='set autoboot=true; add net; set physical=bge0; set address=10.1.1.1; end'
    
    # Boot an already installed zone
    solaris_zone: name=zone1 state=running
    
    # Stop a zone
    solaris_zone: name=zone1 state=stopped
    
    # Destroy a zone
    solaris_zone: name=zone1 state=absent
    
    # Detach a zone
    solaris_zone: name=zone1 state=detached
    
    # Configure a zone, ready to be attached
    solaris_zone: name=zone1 state=configured path=/zones/zone1 root_password="Be9oX7OSwWoU."
          config='set autoboot=true; add net; set physical=bge0; set address=10.1.1.1; end'
    
    # Attach a zone
    solaris_zone: name=zone1 state=attached attach_options='-u'




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

