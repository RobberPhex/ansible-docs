.. _ecs_service:


ecs_service - create, terminate, start or stop a service in ecs
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates or terminates ecs services.


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3
  * botocore
  * json
  * python >= 2.6


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
                <tr><td>aws_access_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS access key. If not set then the value of the AWS_ACCESS_KEY_ID, AWS_ACCESS_KEY or EC2_ACCESS_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_access_key, access_key<div>        </td></tr>
                <tr><td>aws_secret_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS secret key. If not set then the value of the AWS_SECRET_ACCESS_KEY, AWS_SECRET_KEY, or EC2_SECRET_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_secret_key, secret_key<div>        </td></tr>
                <tr><td>client_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Unique, case-sensitive identifier you provide to ensure the idempotency of the request. Up to 32 ASCII characters are allowed.</div>        </td></tr>
                <tr><td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the cluster in which the service exists</div>        </td></tr>
                <tr><td>delay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>The time to wait before checking that the service is available</div>        </td></tr>
                <tr><td>deployment_configuration<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Optional parameters that control the deployment_configuration; format is '{"maximum_percent":&lt;integer&gt;, "minimum_healthy_percent":&lt;integer&gt;}</div>        </td></tr>
                <tr><td>desired_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The count of how many instances of the service. This parameter is required when state=present</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>load_balancers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The list of ELBs defined for this service</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the service</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>repeat<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>The number of times to check that the service is available</div>        </td></tr>
                <tr><td>role<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name or full Amazon Resource Name (ARN) of the IAM role that allows your Amazon ECS container agent to make calls to your load balancer on your behalf. This parameter is only required if you are using a load balancer with your service.</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>deleting</li></ul></td>
        <td><div>The desired state of the service</div>        </td></tr>
                <tr><td>task_definition<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The task definition the service will run. This parameter is required when state=present</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    - ecs_service:
        state: present
        name: console-test-service
        cluster: new_cluster
        task_definition: new_cluster-task:1"
        desired_count: 0
    
    # Basic provisioning example
    - ecs_service:
        name: default
        state: present
        cluster: new_cluster
    
    # Simple example to delete
    - ecs_service:
        name: default
        state: absent
        cluster: new_cluster
    
    # With custom deployment configuration
    - ecs_service:
        name: test-service
        cluster: test-cluster
        task_definition: test-task-definition
        desired_count: 3
        deployment_configuration:
          minimum_healthy_percent: 75
          maximum_percent: 150
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
        <td> ansible_facts </td>
        <td> Facts about deleted service. </td>
        <td align=center> when deleting a service </td>
        <td align=center> complex </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> service </td>
        <td> Details of created service. </td>
        <td align=center> when creating a service </td>
        <td align=center> complex </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - the service role specified must be assumable (i.e. have a trust relationship for the ecs service, ecs.amazonaws.com)
    - for details of the parameters and returns see http://boto3.readthedocs.org/en/latest/reference/services/ecs.html
    - An IAM role must have been previously created
    - If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
    - Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
    - ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
