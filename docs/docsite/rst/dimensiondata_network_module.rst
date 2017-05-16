.. _dimensiondata_network:


dimensiondata_network - Create, update, and delete MCP 1.0 & 2.0 networks
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update, and delete MCP 1.0 & 2.0 networks




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
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Additional description of the network domain.</div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The target datacenter.</div>        </td></tr>
                <tr><td>mcp_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password used to authenticate to the CloudControl API.</div><div>If not specified, will fall back to <code>MCP_PASSWORD</code> from environment variable or <code>~/.dimensiondata</code>.</div><div>Required if <em>mcp_user</em> is specified.</div>        </td></tr>
                <tr><td>mcp_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username used to authenticate to the CloudControl API.</div><div>If not specified, will fall back to <code>MCP_USER</code> from environment variable or <code>~/.dimensiondata</code>.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the network domain to create.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>na</td>
        <td><ul><li>Regions are defined in Apache libcloud project [libcloud/common/dimensiondata.py]</li><li>They are also listed in U(https://libcloud.readthedocs.io/en/latest/compute/drivers/dimensiondata.html)</li><li>Note that the default value "na" stands for "North America".</li><li>The module prepends 'dd-' to the region choice.</li></ul></td>
        <td><div>The target region.</div>        </td></tr>
                <tr><td>service_plan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ESSENTIALS</td>
        <td><ul><li>ESSENTIALS</li><li>ADVANCED</li></ul></td>
        <td><div>The service plan, either “ESSENTIALS” or “ADVANCED”.</div><div>MCP 2.0 Only.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Should the resource be present or absent.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>If <code>false</code>, SSL certificates will not be validated.</div><div>This should only be used on private instances of the CloudControl API that use self-signed certificates.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Should we wait for the task to complete before moving onto the next.</div>        </td></tr>
                <tr><td>wait_poll_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td></td>
        <td><div>The amount of time (in seconds) to wait between checks for task completion.</div><div>Only applicable if <em>wait=true</em>.</div>        </td></tr>
                <tr><td>wait_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td></td>
        <td><div>The maximum amount of time (in seconds) to wait for the task to complete.</div><div>Only applicable if <em>wait=true</em>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create an MCP 1.0 network
    - dimensiondata_network:
        region: na
        location: NA5
        name: mynet
    # Create an MCP 2.0 network
    - dimensiondata_network:
        region: na
        mcp_user: my_user
        mcp_password: my_password
        location: NA9
        name: mynet
        service_plan: ADVANCED
    # Delete a network
    - dimensiondata_network:
        region: na
        location: NA1
        name: mynet
        state: absent

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
        <td> network </td>
        <td> Dictionary describing the network. </td>
        <td align=center> On success when I(state=present). </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> status </td>
        <td> Network status. (MCP 2.0 only) </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> NORMAL </td>
        </tr>
                <tr>
        <td> multicast </td>
        <td> Multicast enabled? (MCP 1.0 only) </td>
        <td align=center>  </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> description </td>
        <td> Network description. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> My network description </td>
        </tr>
                <tr>
        <td> private_net </td>
        <td> Private network subnet. (MCP 1.0 only) </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 10.2.3.0 </td>
        </tr>
                <tr>
        <td> name </td>
        <td> Network name. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> My network </td>
        </tr>
                <tr>
        <td> id </td>
        <td> Network ID. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 8c787000-a000-4050-a215-280893411a7d </td>
        </tr>
                <tr>
        <td> location </td>
        <td> Datacenter location. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> NA3 </td>
        </tr>
        
        </table>
    </td></tr>

        
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
