.. _cs_user:


cs_user - Manages users on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update, disable, lock, enable and remove users.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * cs >= 0.6.10


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
                <tr><td>account<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Account the user will be created under.</div><div>Required on <code>state=present</code>.</div>        </td></tr>
                <tr><td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div>        </td></tr>
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>API key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div>        </td></tr>
                <tr><td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secret key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>HTTP timeout.</div>        </td></tr>
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ROOT</td>
        <td></td>
        <td><div>Domain the user is related to.</div>        </td></tr>
                <tr><td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Email of the user.</div><div>Required on <code>state=present</code>.</div>        </td></tr>
                <tr><td>first_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>First name of the user.</div><div>Required on <code>state=present</code>.</div>        </td></tr>
                <tr><td>last_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Last name of the user.</div><div>Required on <code>state=present</code>.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of the user to be created.</div><div>Required on <code>state=present</code>.</div><div>Only considered on creation and will not be updated if user exists.</div>        </td></tr>
                <tr><td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Poll async jobs until job has finished.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>enabled</li><li>disabled</li><li>locked</li><li>unlocked</li></ul></td>
        <td><div>State of the user.</div><div><code>unlocked</code> is an alias for <code>enabled</code>.</div>        </td></tr>
                <tr><td>timezone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Timezone of the user.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Username of the user.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # create an user in domain 'CUSTOMERS'
    local_action:
      module: cs_user
      account: developers
      username: johndoe
      password: S3Cur3
      last_name: Doe
      first_name: John
      email: john.doe@example.com
      domain: CUSTOMERS
    
    # Lock an existing user in domain 'CUSTOMERS'
    local_action:
      module: cs_user
      username: johndoe
      domain: CUSTOMERS
      state: locked
    
    # Disable an existing user in domain 'CUSTOMERS'
    local_action:
      module: cs_user
      username: johndoe
      domain: CUSTOMERS
      state: disabled
    
    # Enable/unlock an existing user in domain 'CUSTOMERS'
    local_action:
      module: cs_user
      username: johndoe
      domain: CUSTOMERS
      state: enabled
    
    # Remove an user in domain 'CUSTOMERS'
    local_action:
      module: cs_user
      name: customer_xy
      domain: CUSTOMERS
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
        <td> username </td>
        <td> Username of the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> johndoe </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account name of the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> developers </td>
    </tr>
            <tr>
        <td> last_name </td>
        <td> Last name of the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Doe </td>
    </tr>
            <tr>
        <td> account_type </td>
        <td> Type of the account. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> user </td>
    </tr>
            <tr>
        <td> created </td>
        <td> Date the user was created. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Doe </td>
    </tr>
            <tr>
        <td> fist_name </td>
        <td> First name of the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> John </td>
    </tr>
            <tr>
        <td> domain </td>
        <td> Domain the user is related. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ROOT </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 87b1e0ce-4e01-11e4-bb66-0050569e64b8 </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> enabled </td>
    </tr>
            <tr>
        <td> api_secret </td>
        <td> API secret of the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> FUELo3LB9fa1UopjTLPdqLv_6OXQMJZv9g9N4B_Ao3HFz8d6IGFCV9MbPFNM8mwz00wbMevja1DoUNDvI8C9-g </td>
    </tr>
            <tr>
        <td> timezone </td>
        <td> Timezone of the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> enabled </td>
    </tr>
            <tr>
        <td> api_key </td>
        <td> API key of the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> JLhcg8VWi8DoFqL2sSLZMXmGojcLnFrOBTipvBHJjySODcV4mCOo29W2duzPv5cALaZnXj5QxDx3xQfaQt3DKg </td>
    </tr>
            <tr>
        <td> email </td>
        <td> Emailof the user. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> john.doe@example.com </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
    - A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
    - This module supports check mode.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
