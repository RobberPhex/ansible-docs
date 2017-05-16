.. _ufw:


ufw - Manage firewall with UFW
++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage firewall with UFW.


Requirements
------------

  * ``ufw`` package


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
    <td>delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Delete rule.</div></td></tr>
            <tr>
    <td>direction<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>in</li><li>out</li><li>incoming</li><li>outgoing</li><li>routed</li></ul></td>
        <td><div>Select direction for a rule or default policy command.</div></td></tr>
            <tr>
    <td>from_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>any</td>
        <td><ul></ul></td>
        <td><div>Source IP address.</div></br>
        <div style="font-size: small;">aliases: from, src<div></td></tr>
            <tr>
    <td>from_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Source port.</div></td></tr>
            <tr>
    <td>insert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Insert the corresponding rule as rule number NUM</div></td></tr>
            <tr>
    <td>interface<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify interface for rule.</div></br>
        <div style="font-size: small;">aliases: if<div></td></tr>
            <tr>
    <td>log<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Log new connections matched to this rule</div></td></tr>
            <tr>
    <td>logging<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li><li>low</li><li>medium</li><li>high</li><li>full</li></ul></td>
        <td><div>Toggles logging. Logged packets use the LOG_KERN syslog facility.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use profile located in <code>/etc/ufw/applications.d</code></div></br>
        <div style="font-size: small;">aliases: app<div></td></tr>
            <tr>
    <td>policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>allow</li><li>deny</li><li>reject</li></ul></td>
        <td><div>Change the default policy for incoming or outgoing traffic.</div></td></tr>
            <tr>
    <td>proto<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>any</li><li>tcp</li><li>udp</li><li>ipv6</li><li>esp</li><li>ah</li></ul></td>
        <td><div>TCP/IP protocol.</div></td></tr>
            <tr>
    <td>route<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Apply the rule to routed/forwarded packets.</div></td></tr>
            <tr>
    <td>rule<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>allow</li><li>deny</li><li>reject</li><li>limit</li></ul></td>
        <td><div>Add firewall rule</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li><li>reloaded</li><li>reset</li></ul></td>
        <td><div><code>enabled</code> reloads firewall and enables firewall on boot.</div><div><code>disabled</code> unloads firewall and disables firewall on boot.</div><div><code>reloaded</code> reloads firewall.</div><div><code>reset</code> disables and resets firewall to installation defaults.</div></td></tr>
            <tr>
    <td>to_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>any</td>
        <td><ul></ul></td>
        <td><div>Destination IP address.</div></br>
        <div style="font-size: small;">aliases: to, dest<div></td></tr>
            <tr>
    <td>to_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Destination port.</div></br>
        <div style="font-size: small;">aliases: port<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Allow everything and enable UFW
    ufw: state=enabled policy=allow
    
    # Set logging
    ufw: logging=on
    
    # Sometimes it is desirable to let the sender know when traffic is
    # being denied, rather than simply ignoring it. In these cases, use
    # reject instead of deny. In addition, log rejected connections:
    ufw: rule=reject port=auth log=yes
    
    # ufw supports connection rate limiting, which is useful for protecting
    # against brute-force login attacks. ufw will deny connections if an IP
    # address has attempted to initiate 6 or more connections in the last
    # 30 seconds. See  http://www.debian-administration.org/articles/187
    # for details. Typical usage is:
    ufw: rule=limit port=ssh proto=tcp
    
    # Allow OpenSSH
    ufw: rule=allow name=OpenSSH
    
    # Delete OpenSSH rule
    ufw: rule=allow name=OpenSSH delete=yes
    
    # Deny all access to port 53:
    ufw: rule=deny port=53
    
    # Allow all access to tcp port 80:
    ufw: rule=allow port=80 proto=tcp
    
    # Allow all access from RFC1918 networks to this host:
    ufw: rule=allow src={{ item }}
    with_items:
    - 10.0.0.0/8
    - 172.16.0.0/12
    - 192.168.0.0/16
    
    # Deny access to udp port 514 from host 1.2.3.4:
    ufw: rule=deny proto=udp src=1.2.3.4 port=514
    
    # Allow incoming access to eth0 from 1.2.3.5 port 5469 to 1.2.3.4 port 5469
    ufw: rule=allow interface=eth0 direction=in proto=udp src=1.2.3.5 from_port=5469 dest=1.2.3.4 to_port=5469
    
    # Deny all traffic from the IPv6 2001:db8::/32 to tcp port 25 on this host.
    # Note that IPv6 must be enabled in /etc/default/ufw for IPv6 firewalling to work.
    ufw: rule=deny proto=tcp src=2001:db8::/32 port=25
    
    # Deny forwarded/routed traffic from subnet 1.2.3.0/24 to subnet 4.5.6.0/24.
    # Can be used to further restrict a global FORWARD policy set to allow
    ufw: rule=deny route=yes src=1.2.3.0/24 dest=4.5.6.0/24


Notes
-----

.. note:: See ``man ufw`` for more examples.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

