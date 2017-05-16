.. _serverless:


serverless - Manages a Serverless Framework project
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Provides support for managing Serverless Framework (https://serverless.com/) project deployments and stacks.


Requirements (on host that executes module)
-------------------------------------------

  * serverless


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
                <tr><td>deploy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Whether or not to deploy artifacts after building them. When this option is `false` all the functions will be built, but no stack update will be run to send them out. This is mostly useful for generating artifacts to be stored/deployed elsewhere.</div>        </td></tr>
                <tr><td>functions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of specific functions to deploy. If this is not provided, all functions in the service will be deployed.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>us-east-1</td>
        <td></td>
        <td><div>AWS region to deploy the service to</div>        </td></tr>
                <tr><td>service_path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The path to the root of the Serverless Service to be operated on.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Goal state of given stage/project</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic deploy of a service
    - serverless:
        service_path: '{{ project_dir }}'
        state: present
    
    # Deploy specific functions
    - serverless:
        service_path: '{{ project_dir }}'
        functions:
          - my_func_one
          - my_func_two
    
    # deploy a project, then pull its resource list back into Ansible
    - serverless:
        stage: dev
        region: us-east-1
        service_path: '{{ project_dir }}'
      register: sls
    # The cloudformation stack is always named the same as the full service, so the
    # cloudformation_facts module can get a full list of the stack resources, as
    # well as stack events and outputs
    - cloudformation_facts:
        region: us-east-1
        stack_name: '{{ sls.service_name }}'
        stack_resources: true

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
        <td> service_name </td>
        <td> Most </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> my-fancy-service-dev </td>
    </tr>
            <tr>
        <td> state </td>
        <td> Whether the stack for the serverless project is present/absent. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> command </td>
        <td> Full `serverless` command run by this module, in case you want to re-run the command outside the module. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> serverless deploy --stage production </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Currently, the `serverless` command must be in the path of the node executing the task. In the future this may be a flag.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
