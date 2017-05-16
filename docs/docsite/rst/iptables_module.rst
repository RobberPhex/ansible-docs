.. _iptables:


iptables - Modify the systems iptables
++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Iptables is used to set up, maintain, and inspect the tables of IP packet filter rules in the Linux kernel. This module does not handle the saving and/or loading of rules, but rather only manipulates the current rules that are present in memory. This is the same as the behaviour of the "iptables" and "ip6tables" command which this module uses internally.




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
                <tr><td>action<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>append</td>
        <td><ul><li>append</li><li>insert</li></ul></td>
        <td><div>Whether the rule should be appended at the bottom or inserted at the top. If the rule already exists the chain won't be modified.</div>        </td></tr>
                <tr><td>chain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Chain to operate on. This option can either be the name of a user defined chain or any of the builtin chains: 'INPUT', 'FORWARD', 'OUTPUT', 'PREROUTING', 'POSTROUTING', 'SECMARK', 'CONNSECMARK'.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This specifies a comment that will be added to the rule</div>        </td></tr>
                <tr><td>ctstate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>ctstate is a list of the connection states to match in the conntrack module. Possible states are: 'INVALID', 'NEW', 'ESTABLISHED', 'RELATED', 'UNTRACKED', 'SNAT', 'DNAT'</div>        </td></tr>
                <tr><td>destination<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Destination specification. Address can be either a network name, a hostname, a network IP address (with /mask), or a plain IP address. Hostnames will be resolved once only, before the rule is submitted to the kernel. Please note that specifying any name to be resolved with a remote query such as DNS is a really bad idea. The mask can be either a network mask or a plain number, specifying the number of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent to 255.255.255.0. A "!" argument before the address specification inverts the sense of the address.</div>        </td></tr>
                <tr><td>destination_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Destination port or port range specification. This can either be a service name or a port number. An inclusive range can also be specified, using the format first:last. If the first port is omitted, '0' is assumed; if the last is omitted, '65535' is assumed. If the first port is greater than the second one they will be swapped.</div>        </td></tr>
                <tr><td>flush<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Flushes the specified table and chain of all rules. If no chain is specified then the entire table is purged. Ignores all other parameters.</div>        </td></tr>
                <tr><td>fragment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This means that the rule only refers to second and further fragments of fragmented packets. Since there is no way to tell the source or destination ports of such a packet (or ICMP type), such a packet will not match any rules which specify them. When the "!" argument precedes fragment argument, the rule will only match head fragments, or unfragmented packets.</div>        </td></tr>
                <tr><td>goto<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This specifies that the processing should continue in a user specified chain. Unlike the jump argument return will not continue processing in this chain but instead in the chain that called us via jump.</div>        </td></tr>
                <tr><td>icmp_type<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This allows specification of the ICMP type, which can be a numeric ICMP type, type/code pair, or one of the ICMP type names shown by the command 'iptables -p icmp -h'</div>        </td></tr>
                <tr><td>in_interface<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of an interface via which a packet was received (only for packets entering the INPUT, FORWARD and PREROUTING chains). When the "!" argument is used before the interface name, the sense is inverted. If the interface name ends in a "+", then any interface which begins with this name will match. If this option is omitted, any interface name will match.</div>        </td></tr>
                <tr><td>ip_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ipv4</td>
        <td><ul><li>ipv4</li><li>ipv6</li></ul></td>
        <td><div>Which version of the IP protocol this rule should apply to.</div>        </td></tr>
                <tr><td>jump<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This specifies the target of the rule; i.e., what to do if the packet matches it. The target can be a user-defined chain (other than the one this rule is in), one of the special builtin targets which decide the fate of the packet immediately, or an extension (see EXTENSIONS below).  If this option is omitted in a rule (and the goto paramater is not used), then matching the rule will have no effect on the packet's fate, but the counters on the rule will be incremented.</div>        </td></tr>
                <tr><td>limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the maximum average number of matches to allow per second. The number can specify units explicitly, using `/second', `/minute', `/hour' or `/day', or parts of them (so `5/second' is the same as `5/s').</div>        </td></tr>
                <tr><td>limit_burst<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the maximum burst before the above limit kicks in.</div>        </td></tr>
                <tr><td>match<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies a match to use, that is, an extension module that tests for a specific property. The set of matches make up the condition under which a target is invoked. Matches are evaluated first to last if specified as an array and work in short-circuit fashion, i.e. if one extension yields false, evaluation will stop.</div>        </td></tr>
                <tr><td>out_interface<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of an interface via which a packet is going to be sent (for packets entering the FORWARD, OUTPUT and POSTROUTING chains). When the "!" argument is used before the interface name, the sense is inverted. If the interface name ends in a "+", then any interface which begins with this name will match. If this option is omitted, any interface name will match.</div>        </td></tr>
                <tr><td>policy<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set the policy for the chain to the given target. Valid targets are ACCEPT, DROP, QUEUE, RETURN. Only built in chains can have policies. This parameter requires the chain parameter. Ignores all other parameters.</div>        </td></tr>
                <tr><td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The protocol of the rule or of the packet to check. The specified protocol can be one of tcp, udp, udplite, icmp, esp, ah, sctp or the special keyword "all", or it can be a numeric value, representing one of these protocols or a different one. A protocol name from /etc/protocols is also allowed. A "!" argument before the protocol inverts the test.  The number zero is equivalent to all. "all" will match with all protocols and is taken as default when this option is omitted.</div>        </td></tr>
                <tr><td>reject_with<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the error packet type to return while rejecting.</div>        </td></tr>
                <tr><td>set_counters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This enables the administrator to initialize the packet and byte counters of a rule (during INSERT, APPEND, REPLACE operations).</div>        </td></tr>
                <tr><td>set_dscp_mark<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This allows specifying a DSCP mark to be added to packets. It takes either an integer or hex value. Mutually exclusive with <code>set_dscp_mark_class</code>.</div>        </td></tr>
                <tr><td>set_dscp_mark_class<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This allows specifying a predefined DiffServ class which will be translated to the corresponding DSCP mark. Mutually exclusive with <code>set_dscp_mark</code>.</div>        </td></tr>
                <tr><td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Source specification. Address can be either a network name, a hostname, a network IP address (with /mask), or a plain IP address. Hostnames will be resolved once only, before the rule is submitted to the kernel. Please note that specifying any name to be resolved with a remote query such as DNS is a really bad idea. The mask can be either a network mask or a plain number, specifying the number of 1's at the left side of the network mask. Thus, a mask of 24 is equivalent to 255.255.255.0. A "!" argument before the address specification inverts the sense of the address.</div>        </td></tr>
                <tr><td>source_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Source port or port range specification. This can either be a service name or a port number. An inclusive range can also be specified, using the format first:last. If the first port is omitted, '0' is assumed; if the last is omitted, '65535' is assumed. If the first port is greater than the second one they will be swapped.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the rule should be absent or present.</div>        </td></tr>
                <tr><td>table<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>filter</td>
        <td><ul><li>filter</li><li>nat</li><li>mangle</li><li>raw</li><li>security</li></ul></td>
        <td><div>This option specifies the packet matching table which the command should operate on. If the kernel is configured with automatic module loading, an attempt will be made to load the appropriate module for that table if it is not already there.</div>        </td></tr>
                <tr><td>to_destination<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This specifies a destination address to use with DNAT: without this, the destination address is never altered.</div>        </td></tr>
                <tr><td>to_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This specifies a destination port or range of ports to use: without this, the destination port is never altered. This is only valid if the rule also specifies one of the following protocols: tcp, udp, dccp or sctp.</div>        </td></tr>
                <tr><td>to_source<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This specifies a source address to use with SNAT: without this, the source address is never altered.</div>        </td></tr>
                <tr><td>uid_owner<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the UID or username to use in match by owner rule.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Block specific IP
    - iptables:
        chain: INPUT
        source: 8.8.8.8
        jump: DROP
      become: yes
    
    # Forward port 80 to 8600
    - iptables:
        table: nat
        chain: PREROUTING
        in_interface: eth0
        protocol: tcp
        match: tcp
        destination_port: 80
        jump: REDIRECT
        to_ports: 8600
        comment: Redirect web traffic to port 8600
      become: yes
    
    # Allow related and established connections
    - iptables:
        chain: INPUT
        ctstate: ESTABLISHED,RELATED
        jump: ACCEPT
      become: yes
    
    # Tag all outbound tcp packets with DSCP mark 8
    - iptables:
        chain: OUTPUT
        jump: DSCP
        table: mangle
        set_dscp_mark: 8
        protocol: tcp
    
    # Tag all outbound tcp packets with DSCP DiffServ class CS1
    - iptables:
        chain: OUTPUT
        jump: DSCP
        table: mangle
        set_dscp_mark_class: CS1
        protocol: tcp


Notes
-----

.. note::
    - This module just deals with individual rules. If you need advanced chaining of rules the recommended way is to template the iptables restore file.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
