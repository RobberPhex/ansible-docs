.. _netapp_e_volume_copy:


netapp_e_volume_copy - Create volume copy pairs
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create and delete snapshots images on volume groups for NetApp E-series storage arrays.




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
                <tr><td>api_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password to authenticate with the SANtricity WebServices Proxy or embedded REST API.</div>        </td></tr>
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The url to the SANtricity WebServices Proxy or embedded REST API, for example <code>https://prod-1.wahoo.acme.com/devmgr/v2</code>.</div>        </td></tr>
                <tr><td>api_username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username to authenticate with the SANtricity WebServices Proxy or embedded REST API.</div>        </td></tr>
                <tr><td>create_copy_pair_if_does_not_exist<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Defines if a copy pair will be created if it does not exist.</div><div>If set to True destination_volume_id and source_volume_id are required.</div>        </td></tr>
                <tr><td>destination_volume_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The the id of the volume copy destination.</div><div>If used, must be paired with source_volume_id</div><div>Mutually exclusive with volume_copy_pair_id, and search_volume_id</div>        </td></tr>
                <tr><td>search_volume_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Searches for all valid potential target and source volumes that could be used in a copy_pair</div><div>Mutually exclusive with volume_copy_pair_id, destination_volume_id and source_volume_id</div>        </td></tr>
                <tr><td>source_volume_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The the id of the volume copy source.</div><div>If used, must be paired with destination_volume_id</div><div>Mutually exclusive with volume_copy_pair_id, and search_volume_id</div>        </td></tr>
                <tr><td>start_stop_copy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>starts a re-copy or stops a copy in progress</div><div>Note: If you stop the initial file copy before it it done the copy pair will be destroyed</div><div>Requires volume_copy_pair_id</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified volume copy pair should exist or not.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Should https certificates be validated?</div>        </td></tr>
                <tr><td>volume_copy_pair_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The the id of a given volume copy pair</div><div>Mutually exclusive with destination_volume_id, source_volume_id, and search_volume_id</div><div>Can use to delete or check presence of volume pairs</div><div>Must specify this or (destination_volume_id and source_volume_id)</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    msg:
        description: Success message
        returned: success
        type: string
        sample: Json facts for the volume copy that was created.

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
        <td> msg </td>
        <td> Success message </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Created Volume Copy Pair with ID </td>
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
