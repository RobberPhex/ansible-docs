.. _apache2_mod_proxy:


apache2_mod_proxy - Set and/or get members' attributes of an Apache httpd 2.4 mod_proxy balancer pool
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Set and/or get members' attributes of an Apache httpd 2.4 mod_proxy balancer pool, using HTTP POST and GET requests. The httpd mod_proxy balancer-member status page has to be enabled and accessible, as this module relies on parsing this page. This module supports ansible check_mode, and requires BeautifulSoup python module.




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
    <td>balancer_url_suffix<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/balancer-manager/</td>
        <td><ul></ul></td>
        <td><div>Suffix of the balancer pool url required to access the balancer pool status page (e.g. balancer_vhost[:port]/balancer_url_suffix).</div></td></tr>
            <tr>
    <td>balancer_vhost<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>(ipv4|ipv6|fqdn):port of the Apache httpd 2.4 mod_proxy balancer pool.</div></td></tr>
            <tr>
    <td>member_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>(ipv4|ipv6|fqdn) of the balancer member to get or to set attributes to. Port number is autodetected and should not be specified here. If undefined, apache2_mod_proxy module will return a members list of dictionaries of all the current balancer pool members' attributes.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>present</li><li>absent</li><li>enabled</li><li>disabled</li><li>drained</li><li>hot_standby</li><li>ignore_errors</li></ul></td>
        <td><div>Desired state of the member host. (absent|disabled),drained,hot_standby,ignore_errors can be simultaneously invoked by separating them with a comma (e.g. state=drained,ignore_errors).</div></td></tr>
            <tr>
    <td>tls<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Use https to access balancer management page.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Validate ssl/tls certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Get all current balancer pool members' attributes:
    - apache2_mod_proxy: balancer_vhost=10.0.0.2
    
    # Get a specific member's attributes:
    - apache2_mod_proxy: balancer_vhost=myws.mydomain.org balancer_suffix="/lb/" member_host=node1.myws.mydomain.org
    
    # Enable all balancer pool members:
    - apache2_mod_proxy: balancer_vhost="{{ myloadbalancer_host }}"
      register: result
    - apache2_mod_proxy: balancer_vhost="{{ myloadbalancer_host }}" member_host="{{ item.host }}" state=present
      with_items: "{{ result.members }}"
    
    # Gracefully disable a member from a loadbalancer node:
    - apache2_mod_proxy: balancer_vhost="{{ vhost_host }}" member_host="{{ member.host }}" state=drained delegate_to=myloadbalancernode
    - wait_for: host="{{ member.host }}" port={{ member.port }} state=drained delegate_to=myloadbalancernode
    - apache2_mod_proxy: balancer_vhost="{{ vhost_host }}" member_host="{{ member.host }}" state=absent delegate_to=myloadbalancernode

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
        <td> member </td>
        <td> specific balancer member information dictionary, returned when apache2_mod_proxy module is invoked with member_host parameter. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'status': {'disabled': False, 'hot_standby': False, 'drained': False, 'ignore_errors': False}, 'protocol': 'http', 'management_url': 'http://10.10.0.2/lb/?b=mywsbalancer&w=http://10.10.0.20:8080/ws&nonce=8925436c-79c6-4841-8936-e7d13b79239b', 'balancer_url': 'http://10.10.0.2/balancer-manager/', 'host': '10.10.0.20', 'attributes': {'Load': '0', 'Status': 'Init Ok ', 'Busy': '0', 'From': '136K', 'Elected': '42', 'Route': None, 'To': ' 47K', 'Set': '0', 'Factor': '1', 'Worker URL': None, 'RouteRedir': None}, 'path': '/ws', 'port': 8080} </td>
    </tr>
            <tr>
        <td> members </td>
        <td> list of member (defined above) dictionaries, returned when apache2_mod_proxy is invoked with no member_host and state args. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [{'status': {'disabled': False, 'hot_standby': False, 'drained': False, 'ignore_errors': False}, 'protocol': 'http', 'management_url': 'http://10.10.0.2/lb/?b=mywsbalancer&w=http://10.10.0.20:8080/ws&nonce=8925436c-79c6-4841-8936-e7d13b79239b', 'balancer_url': 'http://10.10.0.2/balancer-manager/', 'host': '10.10.0.20', 'attributes': {'Load': '0', 'Status': 'Init Ok ', 'Busy': '0', 'From': '136K', 'Elected': '42', 'Route': None, 'To': ' 47K', 'Set': '0', 'Factor': '1', 'Worker URL': None, 'RouteRedir': None}, 'path': '/ws', 'port': 8080}, {'status': {'disabled': False, 'hot_standby': False, 'drained': False, 'ignore_errors': False}, 'protocol': 'http', 'management_url': 'http://10.10.0.2/lb/?b=mywsbalancer&w=http://10.10.0.21:8080/ws&nonce=8925436c-79c6-4841-8936-e7d13b79239b', 'balancer_url': 'http://10.10.0.2/balancer-manager/', 'host': '10.10.0.21', 'attributes': {'Load': '0', 'Status': 'Init Ok ', 'Busy': '0', 'From': '136K', 'Elected': '42', 'Route': None, 'To': ' 47K', 'Set': '0', 'Factor': '1', 'Worker URL': None, 'RouteRedir': None}, 'path': '/ws', 'port': 8080}] </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

