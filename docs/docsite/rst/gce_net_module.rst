.. _gce_net:


gce_net - create/destroy GCE networks and firewall rules
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module can create and destroy Google Compute Engine networks and firewall rules https://cloud.google.com/compute/docs/networking. The *name* parameter is reserved for referencing a network while the *fwname* parameter is used to reference firewall rules. IPv4 Address ranges must be specified using the CIDR http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing format. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud >= 0.13.3, >= 0.17.0 if using JSON credentials


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
                <tr><td>allowed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the protocol:ports to allow ('tcp:80' or 'tcp:80,443' or 'tcp:80-800;udp:1-25') this parameter is mandatory when creating or updating a firewall rule</div>        </td></tr>
                <tr><td>credentials_file<br/><div style="font-size: small;"> (added in 2.1.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>path to the JSON file associated with the service account email</div>        </td></tr>
                <tr><td>fwname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>name of the firewall rule</div></br>
    <div style="font-size: small;">aliases: fwrule<div>        </td></tr>
                <tr><td>ipv4_range<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the IPv4 address range in CIDR notation for the network this parameter is not mandatory when you specified existing network in name parameter, but when you create new network, this parameter is mandatory</div></br>
    <div style="font-size: small;">aliases: cidr<div>        </td></tr>
                <tr><td>mode<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>legacy</td>
        <td><ul><li>legacy</li><li>auto</li><li>custom</li></ul></td>
        <td><div>network mode for Google Cloud "legacy" indicates a network with an IP address range "auto" automatically generates subnetworks in different regions "custom" uses networks to group subnets of user specified IP address ranges https://cloud.google.com/compute/docs/networking#network_types</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>name of the network</div>        </td></tr>
                <tr><td>pem_file<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>path to the pem file associated with the service account email This option is deprecated. Use 'credentials_file'.</div>        </td></tr>
                <tr><td>project_id<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>your GCE project ID</div>        </td></tr>
                <tr><td>service_account_email<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>service account email</div>        </td></tr>
                <tr><td>src_range<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the source IPv4 address range in CIDR notation</div></br>
    <div style="font-size: small;">aliases: src_cidr<div>        </td></tr>
                <tr><td>src_tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the source instance tags for creating a firewall rule</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>active</li><li>present</li><li>absent</li><li>deleted</li></ul></td>
        <td><div>desired state of the network or firewall</div>        </td></tr>
                <tr><td>subnet_desc<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>description of subnet to create</div>        </td></tr>
                <tr><td>subnet_name<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>name of subnet to create</div>        </td></tr>
                <tr><td>subnet_region<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>region of subnet to create</div>        </td></tr>
                <tr><td>target_tags<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the target instance tags for creating a firewall rule</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a 'legacy' Network
    - name: Create Legacy Network
      gce_net:
        name: legacynet
        ipv4_range: '10.24.17.0/24'
        mode: legacy
        state: present
    
    # Create an 'auto' Network
    - name: Create Auto Network
      gce_net:
        name: autonet
        mode: auto
        state: present
    
    # Create a 'custom' Network
    - name: Create Custom Network
      gce_net:
        name: customnet
        mode: custom
        subnet_name: "customsubnet"
        subnet_region: us-east1
        ipv4_range: '10.240.16.0/24'
        state: "present"
    
    # Create Firewall Rule with Source Tags
    - name: Create Firewall Rule w/Source Tags
      gce_net:
        name: default
        fwname: "my-firewall-rule"
        allowed: tcp:80
        state: "present"
        src_tags: "foo,bar"
    
    # Create Firewall Rule with Source Range
    - name: Create Firewall Rule w/Source Range
      gce_net:
        name: default
        fwname: "my-firewall-rule"
        allowed: tcp:80
        state: "present"
        src_range: ['10.1.1.1/32']
    
    # Create Custom Subnetwork
    - name: Create Custom Subnetwork
      gce_net:
        name: privatenet
        mode: custom
        subnet_name: subnet_example
        subnet_region: us-central1
        ipv4_range: '10.0.0.0/16'

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
        <td> fwname </td>
        <td> Name of the firewall rule. </td>
        <td align=center> When specified </td>
        <td align=center> string </td>
        <td align=center> my-fwname </td>
    </tr>
            <tr>
        <td> subnet_region </td>
        <td> Region of the specified subnet. </td>
        <td align=center> when specified or when a subnetwork is created </td>
        <td align=center> string </td>
        <td align=center> us-east1 </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the network. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> my-network </td>
    </tr>
            <tr>
        <td> src_range </td>
        <td> IP address blocks a firewall rule applies to. </td>
        <td align=center> when specified </td>
        <td align=center> list </td>
        <td align=center> ['10.1.1.12/8'] </td>
    </tr>
            <tr>
        <td> src_tags </td>
        <td> Instance Tags firewall rule applies to. </td>
        <td align=center> when specified while creating a firewall rule </td>
        <td align=center> list </td>
        <td align=center> ['foo', 'bar'] </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the item operated on. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> subnet_name </td>
        <td> Name of the subnetwork. </td>
        <td align=center> when specified or when a subnetwork is created </td>
        <td align=center> string </td>
        <td align=center> my-subnetwork </td>
    </tr>
            <tr>
        <td> allowed </td>
        <td> Rules (ports and protocols) specified by this firewall rule. </td>
        <td align=center> When specified </td>
        <td align=center> string </td>
        <td align=center> tcp:80;icmp </td>
    </tr>
            <tr>
        <td> ipv4_range </td>
        <td> IPv4 range of the specified network or subnetwork. </td>
        <td align=center> when specified or when a subnetwork is created </td>
        <td align=center> string </td>
        <td align=center> 10.0.0.0/16 </td>
    </tr>
            <tr>
        <td> target_tags </td>
        <td> Instance Tags with these tags receive traffic allowed by firewall rule. </td>
        <td align=center> when specified while creating a firewall rule </td>
        <td align=center> list </td>
        <td align=center> ['foo', 'bar'] </td>
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
