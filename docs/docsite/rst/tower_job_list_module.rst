.. _tower_job_list:


tower_job_list - List Ansible Tower jobs.
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* List Ansible Tower jobs. See https://www.ansible.com/tower for an overview.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * ansible-tower-cli >= 3.0.2


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
                <tr><td>all_pages<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Fetch all the pages and return a single result.</div>        </td></tr>
                <tr><td>page<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Page number of the results to fetch.</div>        </td></tr>
                <tr><td>query<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Query used to further filter the list of jobs. {"foo":"bar"} will be passed at ?foo=bar</div>        </td></tr>
                <tr><td>status<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>pending</li><li>waiting</li><li>running</li><li>error</li><li>failed</li><li>canceled</li><li>successful</li></ul></td>
        <td><div>Only list jobs with this status.</div>        </td></tr>
                <tr><td>tower_config_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to the Tower config file. See notes.</div>        </td></tr>
                <tr><td>tower_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL to your Tower instance.</div>        </td></tr>
                <tr><td>tower_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password for your Tower instance.</div>        </td></tr>
                <tr><td>tower_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username for your Tower instance.</div>        </td></tr>
                <tr><td>tower_verify_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Dis/allow insecure connections to Tower. If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: List running jobs for the testing.yml playbook
      tower_job_list:
        status: running
        query: {"playbook": "testing.yml"}
        register: testing_jobs
        tower_config_file: "~/tower_cli.cfg"

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
        <td> count </td>
        <td> Total count of objects return </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> next </td>
        <td> next page available for the listing </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 3 </td>
    </tr>
            <tr>
        <td> results </td>
        <td> a list of job objects represented as dictionaries </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [{'force_handlers': False, 'job_template': 5, 'ask_credential_on_launch': False, 'artifacts': {}, 'ask_job_type_on_launch': False, 'job_tags': '', 'job_type': 'run', 'allow_simultaneous': False, 'failed': False, 'finished': '2017-02-22T15:09:05.633942Z', 'ask_inventory_on_launch': False, 'inventory': 1, 'id': 2, 'forks': 0, 'job_explanation': ''}, '...'] </td>
    </tr>
            <tr>
        <td> previous </td>
        <td> previous page available for the listing </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 1 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - If no *config_file* is provided we will attempt to use the tower-cli library defaults to find your Tower host information.
    - *config_file* should contain Tower configuration in the following format host=hostname username=username password=password



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
