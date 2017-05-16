.. _omapi_host:


omapi_host - Setup OMAPI hosts.
+++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update and remove OMAPI hosts into compatible DHCPd servers.


Requirements (on host that executes module)
-------------------------------------------

  * pypureomapi


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
                <tr><td>ddns<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable dynamic DNS updates for this host.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>Sets OMAPI server host to interact with.</div>        </td></tr>
                <tr><td>ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Sets the lease host IP address.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Sets the TSIG key content for authenticating against OMAPI server.</div>        </td></tr>
                <tr><td>key_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Sets the TSIG key name for authenticating against OMAPI server.</div>        </td></tr>
                <tr><td>macaddr<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Sets the lease host MAC address.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Sets the host lease hostname (mandatory if state=present).</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>7911</td>
        <td></td>
        <td><div>Sets the OMAPI server port to interact with.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or remove OMAPI host.</div>        </td></tr>
                <tr><td>statements<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Attach a list of OMAPI DHCP statements with host lease (without ending semicolon).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Remove a host using OMAPI
      omapi_host:
        key_name: "defomapi"
        key: "+bFQtBCta6j2vWkjPkNFtgA=="
        host: "10.1.1.1"
        macaddr: "00:66:ab:dd:11:44"
        state: absent
    
    - name: Add a host using OMAPI
      omapi_host:
        key_name: "defomapi"
        key: "+bFQtBCta6j2vWkjPkNFtgA=="
        host: "10.98.4.55"
        macaddr: "44:dd:ab:dd:11:44"
        name: "server01"
        ip: "192.168.88.99"
        ddns: yes
        statements:
          - 'filename "pxelinux.0"'
          - 'next-server 1.1.1.1'
        state: present

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
        <td> If module has modified a host </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> lease </td>
        <td> dictionnary containing host informations </td>
        <td align=center> success </td>
        <td align=center> complex </td>
        <td align=center>  </td>
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
