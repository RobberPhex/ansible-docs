.. _consul:


consul - Add, modify & delete services within a consul cluster.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Registers services and checks for an agent with a consul cluster. A service is some process running on the agent node that should be advertised by consul's discovery mechanism. It may optionally supply a check definition, a periodic service test to notify the consul cluster of service's health.
* Checks may also be registered per node e.g. disk usage, or cpu usage and notify the health of the entire node to the cluster. Service level checks do not require a check name or id as these are derived by Consul from the Service name and id respectively by appending 'service:' Node level checks require a check_name and optionally a check_id.
* Currently, there is no complete way to retrieve the script, interval or ttl metadata for a registered check. Without this metadata it is  not possible to tell if the data supplied with ansible represents a change to a check. As a result this does not attempt to determine changes and will always report a changed occurred. An api method is planned to supply this metadata so at that stage change management will be added.
* See http://consul.io for more details.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python-consul
  * requests


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
                <tr><td>check_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>an ID for the service check, defaults to the check name, ignored if part of a service definition.</div>        </td></tr>
                <tr><td>check_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>a name for the service check, defaults to the check id. required if standalone, ignored if part of service definition.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>host of the consul agent defaults to localhost</div>        </td></tr>
                <tr><td>http<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>checks can be registered with an http endpoint. This means that consul will check that the http endpoint returns a successful http status. Interval must also be provided with this option.</div>        </td></tr>
                <tr><td>interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>the interval at which the service check will be run. This is a number with a s or m suffix to signify the units of seconds or minutes e.g 15s or 1m. If no suffix is supplied, m will be used by default e.g. 1 will be 1m. Required if the script param is specified.</div>        </td></tr>
                <tr><td>notes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Notes to attach to check when registering it.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>8500</td>
        <td></td>
        <td><div>the port on which the consul agent is running</div>        </td></tr>
                <tr><td>scheme<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>http</td>
        <td></td>
        <td><div>the protocol scheme on which the consul agent is running</div>        </td></tr>
                <tr><td>script<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>the script/command that will be run periodically to check the health of the service. Scripts require an interval and vise versa</div>        </td></tr>
                <tr><td>service_address<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>the address to advertise that the service will be listening on. This value will be passed as the <em>Address</em> parameter to Consul's <a href='/v1/agent/service/register'>/v1/agent/service/register</a> API method, so refer to the Consul API documentation for further details.</div>        </td></tr>
                <tr><td>service_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>service_name if supplied</td>
        <td></td>
        <td><div>the ID for the service, must be unique per node, defaults to the service name if the service name is supplied</div>        </td></tr>
                <tr><td>service_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Unique name for the service on a node, must be unique per node, required if registering a service. May be omitted if registering a node level check</div>        </td></tr>
                <tr><td>service_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the port on which the service is listening required for registration of a service, i.e. if service_name or service_id is set</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>register or deregister the consul service, defaults to present</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>a list of tags that will be attached to the service registration.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A custom HTTP check timeout. The consul default is 10 seconds. Similar to the interval this is a number with a s or m suffix to signify the units of seconds or minutes, e.g. 15s or 1m.</div>        </td></tr>
                <tr><td>token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>the token key indentifying an ACL rule set. May be required to register services.</div>        </td></tr>
                <tr><td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>checks can be registered with a ttl instead of a script and interval this means that the service will check in with the agent before the ttl expires. If it doesn't the check will be considered failed. Required if registering a check and the script an interval are missing Similar to the interval this is a number with a s or m suffix to signify the units of seconds or minutes e.g 15s or 1m. If no suffix is supplied, m will be used by default e.g. 1 will be 1m</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>whether to verify the tls certificate of the consul agent</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: register nginx service with the local consul agent
      consul:
        service_name: nginx
        service_port: 80
    
    - name: register nginx service with curl check
      consul:
        service_name: nginx
        service_port: 80
        script: curl http://localhost
        interval: 60s
    
    - name: register nginx with an http check
      consul:
        service_name: nginx
        service_port: 80
        interval: 60s
        http: http://localhost:80/status
    
    - name: register external service nginx available at 10.1.5.23
      consul:
        service_name: nginx
        service_port: 80
        service_address: 10.1.5.23
    
    - name: register nginx with some service tags
      consul:
        service_name: nginx
        service_port: 80
        tags:
          - prod
          - webservers
    
    - name: remove nginx service
      consul:
        service_name: nginx
        state: absent
    
    - name: create a node level check to test disk usage
      consul:
        check_name: Disk usage
        check_id: disk_usage
        script: /opt/disk_usage.py
        interval: 5m
    
    - name: register an http check against a service that's already registered
      consul:
        check_name: nginx-check2
        check_id: nginx-check2
        service_id: nginx
        interval: 60s
        http: http://localhost:80/morestatus





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
