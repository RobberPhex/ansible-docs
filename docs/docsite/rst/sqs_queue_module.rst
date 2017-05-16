.. _sqs_queue:


sqs_queue - Creates or deletes AWS SQS queues.
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or delete AWS SQS queues.
* Update attributes on existing queues.


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto >= 2.33.0
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
                <tr><td>default_visibility_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The default visibility timeout in seconds.</div>        </td></tr>
                <tr><td>delivery_delay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The delivery delay in seconds.</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>maximum_message_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The maximum message size in bytes.</div>        </td></tr>
                <tr><td>message_retention_period<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The message retention period in seconds.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the queue.</div>        </td></tr>
                <tr><td>policy<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The json dict policy to attach to queue</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>receive_message_wait_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The receive message wait time in seconds.</div>        </td></tr>
                <tr><td>redrive_policy<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>json dict with the redrive_policy (see example)</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or delete the queue</div>        </td></tr>
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

    # Create SQS queue with redrive policy
    - sqs_queue:
        name: my-queue
        region: ap-southeast-2
        default_visibility_timeout: 120
        message_retention_period: 86400
        maximum_message_size: 1024
        delivery_delay: 30
        receive_message_wait_time: 20
        policy: "{{ json_dict }}"
        redrive_policy:
          maxReceiveCount: 5
          deadLetterTargetArn: arn:aws:sqs:eu-west-1:123456789012:my-dead-queue
    
    # Delete SQS queue
    - sqs_queue:
        name: my-queue
        region: ap-southeast-2
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
        <td> message_retention_period </td>
        <td> The message retention period in seconds. </td>
        <td align=center> always </td>
        <td align=center>  </td>
        <td align=center> 345600 </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the SQS Queue </td>
        <td align=center> always </td>
        <td align=center>  </td>
        <td align=center> queuename-987d2de0 </td>
    </tr>
            <tr>
        <td> delivery_delay </td>
        <td> The delivery delay in seconds. </td>
        <td align=center> always </td>
        <td align=center>  </td>
        <td align=center> 0 </td>
    </tr>
            <tr>
        <td> default_visibility_timeout </td>
        <td> The default visibility timeout in seconds. </td>
        <td align=center> always </td>
        <td align=center>  </td>
        <td align=center> 30 </td>
    </tr>
            <tr>
        <td> region </td>
        <td> Region that the queue was created within </td>
        <td align=center> always </td>
        <td align=center>  </td>
        <td align=center> us-east-1 </td>
    </tr>
            <tr>
        <td> queue_arn </td>
        <td> The queue's Amazon resource name (ARN). </td>
        <td align=center> on successful creation or update of the queue </td>
        <td align=center>  </td>
        <td align=center> arn:aws:sqs:us-east-1:199999999999:queuename-987d2de0 </td>
    </tr>
            <tr>
        <td> maximum_message_size </td>
        <td> The maximum message size in bytes. </td>
        <td align=center> always </td>
        <td align=center>  </td>
        <td align=center> 262144 </td>
    </tr>
            <tr>
        <td> receive_message_wait_time </td>
        <td> The receive message wait time in seconds. </td>
        <td align=center> always </td>
        <td align=center>  </td>
        <td align=center> 0 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
    - Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
    - ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
