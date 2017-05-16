.. _packet_device:


packet_device - create, destroy, start, stop, and reboot a Packet Host machine.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* create, destroy, update, start, stop, and reboot a Packet Host machine. When the machine is created it can optionally wait for it to have an IP address before returning. This module has a dependency on packet >= 1.0.
* API is documented at https://www.packet.net/help/api/#page:devices,header:devices-devices-post.


Requirements (on host that executes module)
-------------------------------------------

  * packet-python
  * python >= 2.6


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
                <tr><td>auth_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Packet api token. You can also supply it in env var <code>PACKET_API_TOKEN</code>.</div>        </td></tr>
                <tr><td>count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of devices to create. Count number can be included in hostname via the %d string formatter.</div>        </td></tr>
                <tr><td>count_offset<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>From which number to start the count.</div>        </td></tr>
                <tr><td>device_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of device IDs on which to operate.</div>        </td></tr>
                <tr><td>facility<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Facility slug for device creation. As of 2016, it should be one of [ewr1, sjc1, ams1, nrt1].</div>        </td></tr>
                <tr><td>features<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dict with "features" for device creation. See Packet API docs for details.</div>        </td></tr>
                <tr><td>hostnames<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hostname of a device, or a list of hostnames.</div><div>If given string or one-item list, you can use the <code>"%d"</code> Python string format to expand numbers from count.</div><div>If only one hostname, it might be expanded to list if count&gt;1.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>lock<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether to lock a created device.</div>        </td></tr>
                <tr><td>operating_system<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>OS slug for device creation. See Packet docs or API for current list.</div>        </td></tr>
                <tr><td>plan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Plan slug for device creation. See Packet docs or API for current list.</div>        </td></tr>
                <tr><td>project_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>ID of project of the device.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>active</li><li>inactive</li><li>rebooted</li></ul></td>
        <td><div>Desired state of the device.</div>        </td></tr>
                <tr><td>user_data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Userdata blob made available to the machine</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to wait for the instance to be assigned IP address before returning.</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>60</td>
        <td></td>
        <td><div>How long to wait for IP address of new devices before quitting. In seconds.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # All the examples assume that you have your Packet api token in env var PACKET_API_TOKEN.
    # You can also pass it to the auth_token parameter of the module instead.
    
    # Creating devices
    
    - name: create 1 device
      hosts: localhost
      tasks:
      - packet_device:
          project_id: 89b497ee-5afc-420a-8fb5-56984898f4df
          hostnames: myserver
          operating_system: ubuntu_16_04
          plan: baremetal_0
          facility: sjc1
    
    - name: create 3 ubuntu devices called server-01, server-02 and server-03
      hosts: localhost
      tasks:
      - packet_device:
          project_id: 89b497ee-5afc-420a-8fb5-56984898f4df
          hostnames: server-%02d
          count: 3
          operating_system: ubuntu_16_04
          plan: baremetal_0
          facility: sjc1
    
    - name: Create 3 coreos devices with userdata, wait until they get IPs and then wait for SSH
      hosts: localhost
      tasks:
      - name: create 3 devices and register their facts
        packet_device:
          hostnames: [coreos-one, coreos-two, coreos-three]
          operating_system: coreos_stable
          plan: baremetal_0
          facility: ewr1
          locked: true
          project_id: 89b497ee-5afc-420a-8fb5-56984898f4df
          user_data: |
            #cloud-config
            ssh_authorized_keys:
              - ssh-dss AAAAB3NzaC1kc3MAAACBAIfNT5S0ncP4BBJBYNhNPxFF9lqVhfPeu6SM1LoCocxqDc1AT3zFRi8hjIf6TLZ2AA4FYbcAWxLMhiBxZRVldT9GdBXile78kAK5z3bKTwq152DCqpxwwbaTIggLFhsU8wrfBsPWnDuAxZ0h7mmrCjoLIE3CNLDA/NmV3iB8xMThAAAAFQCStcesSgR1adPORzBxTr7hug92LwAAAIBOProm3Gk+HWedLyE8IfofLaOeRnbBRHAOL4z0SexKkVOnQ/LGN/uDIIPGGBDYTvXgKZT+jbHeulRJ2jKgfSpGKN4JxFQ8uzVH492jEiiUJtT72Ss1dCV4PmyERVIw+f54itihV3z/t25dWgowhb0int8iC/OY3cGodlmYb3wdcQAAAIBuLbB45djZXzUkOTzzcRDIRfhaxo5WipbtEM2B1fuBt2gyrvksPpH/LK6xTjdIIb0CxPu4OCxwJG0aOz5kJoRnOWIXQGhH7VowrJhsqhIc8gN9ErbO5ea8b1L76MNcAotmBDeTUiPw01IJ8MdDxfmcsCslJKgoRKSmQpCwXQtN2g== tomk@hp2
            coreos:
              etcd:
                discovery: https://discovery.etcd.io/6a28e078895c5ec737174db2419bb2f3
                addr: $private_ipv4:4001
                peer-addr: $private_ipv4:7001
              fleet:
                public-ip: $private_ipv4
              units:
                - name: etcd.service
                  command: start
                - name: fleet.service
                  command: start
        register: newhosts
    
      - name: wait for ssh
        wait_for:
          delay: 1
          host: "{{ item.public_ipv4 }}"
          port: 22
          state: started
          timeout: 500
        with_items: "{{ newhosts.devices }}"
    
    
    # Other states of devices
    
    - name: remove 3 devices by uuid
      hosts: localhost
      tasks:
      - packet_device:
          project_id: 89b497ee-5afc-420a-8fb5-56984898f4df
          state: absent
          device_ids:
            - 1fb4faf8-a638-4ac7-8f47-86fe514c30d8
            - 2eb4faf8-a638-4ac7-8f47-86fe514c3043
            - 6bb4faf8-a638-4ac7-8f47-86fe514c301f

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
        <td> changed </td>
        <td> True if a device was altered in any way (created, modified or removed) </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> devices </td>
        <td> Information about each device that was processed </td>
        <td align=center> always </td>
        <td align=center> array </td>
        <td align=center> [{"hostname": "my-server.com", "id": "server-id", "public-ipv4": "147.229.15.12", "private-ipv4": "10.0.15.12", "public-ipv6": ""2604:1380:2:5200::3"}] </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
