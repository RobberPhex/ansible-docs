.. _win_dns_client:


win_dns_client - Configures DNS lookup on Windows hosts
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``win_dns_client`` module configures the DNS client on Windows network adapters.




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
                <tr><td>adapter_names<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Adapter name or list of adapter names for which to manage DNS settings ('*' is supported as a wildcard value). The adapter name used is the connection caption in the Network Control Panel or via <code>Get-NetAdapter</code>, eg <code>Local Area Connection</code>.</div>        </td></tr>
                <tr><td>ipv4_addresses<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Single or ordered list of DNS server IPv4 addresses to configure for lookup. An empty list will configure the adapter to use the DHCP-assigned values on connections where DHCP is enabled, or disable DNS lookup on statically-configured connections.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      # set a single address on the adapter named Ethernet
      - win_dns_client:
          adapter_names: Ethernet
          ipv4_addresses: 192.168.34.5
    
      # set multiple lookup addresses on all visible adapters (usually physical adapters that are in the Up state), with debug logging to a file
      - win_dns_client:
          adapter_names: "*"
          ipv4_addresses:
          - 192.168.34.5
          - 192.168.34.6
          log_path: c:\dns_log.txt
    
      # configure all adapters whose names begin with Ethernet to use DHCP-assigned DNS values
      - win_dns_client:
          adapter_names: "Ethernet*"
          ipv4_addresses: []


Notes
-----

.. note::
    - When setting an empty list of DNS server addresses on an adapter with DHCP enabled, a change will always be registered, since it is not possible to detect the difference between a DHCP-sourced server value and one that is statically set.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
