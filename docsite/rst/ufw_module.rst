.. _ufw:


ufw - Manage firewall with UFW
++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Manage firewall with UFW.

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
    <td>delete</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Delete rule.</td>
    </tr>
            <tr>
    <td>direction</td>
    <td>no</td>
    <td></td>
        <td><ul><li>in</li><li>out</li><li>incoming</li><li>outgoing</li><li>routed</li></ul></td>
        <td>Select direction for a rule or default policy command.</td>
    </tr>
            <tr>
    <td>from_ip</td>
    <td>no</td>
    <td>any</td>
        <td><ul></ul></td>
        <td>Source IP address.</td>
    </tr>
            <tr>
    <td>from_port</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Source port.</td>
    </tr>
            <tr>
    <td>insert</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Insert the corresponding rule as rule number NUM</td>
    </tr>
            <tr>
    <td>interface</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specify interface for rule.</td>
    </tr>
            <tr>
    <td>log</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Log new connections matched to this rule</td>
    </tr>
            <tr>
    <td>logging</td>
    <td>no</td>
    <td></td>
        <td><ul><li>on</li><li>off</li><li>low</li><li>medium</li><li>high</li><li>full</li></ul></td>
        <td>Toggles logging. Logged packets use the LOG_KERN syslog facility.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Use profile located in <code>/etc/ufw/applications.d</code></td>
    </tr>
            <tr>
    <td>policy</td>
    <td>no</td>
    <td></td>
        <td><ul><li>allow</li><li>deny</li><li>reject</li></ul></td>
        <td>Change the default policy for incoming or outgoing traffic.</td>
    </tr>
            <tr>
    <td>proto</td>
    <td>no</td>
    <td></td>
        <td><ul><li>any</li><li>tcp</li><li>udp</li><li>ipv6</li><li>esp</li><li>ah</li></ul></td>
        <td>TCP/IP protocol.</td>
    </tr>
            <tr>
    <td>rule</td>
    <td>no</td>
    <td></td>
        <td><ul><li>allow</li><li>deny</li><li>reject</li><li>limit</li></ul></td>
        <td>Add firewall rule</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li><li>reloaded</li><li>reset</li></ul></td>
        <td><code>enabled</code> reloads firewall and enables firewall on boot.<code>disabled</code> unloads firewall and disables firewall on boot.<code>reloaded</code> reloads firewall.<code>reset</code> disables and resets firewall to installation defaults.</td>
    </tr>
            <tr>
    <td>to_ip</td>
    <td>no</td>
    <td>any</td>
        <td><ul></ul></td>
        <td>Destination IP address.</td>
    </tr>
            <tr>
    <td>to_port</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Destination port.</td>
    </tr>
        </table>


.. note:: Requires ``ufw`` package


Examples
--------

.. raw:: html

    <br/>


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

.. note:: See ``man ufw`` for more examples.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

