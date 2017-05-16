.. _execute_lambda:


execute_lambda - Execute an AWS Lambda function
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module executes AWS Lambda functions, allowing synchronous and asynchronous invocation.


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3
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
            <tr>
    <td>aws_access_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS access key. If not set then the value of the AWS_ACCESS_KEY_ID, AWS_ACCESS_KEY or EC2_ACCESS_KEY environment variable is used.</div></br>
        <div style="font-size: small;">aliases: ec2_access_key, access_key<div></td></tr>
            <tr>
    <td>aws_secret_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS secret key. If not set then the value of the AWS_SECRET_ACCESS_KEY, AWS_SECRET_KEY, or EC2_SECRET_KEY environment variable is used.</div></br>
        <div style="font-size: small;">aliases: ec2_secret_key, secret_key<div></td></tr>
            <tr>
    <td>dry_run<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Do not *actually* invoke the function. A <code>DryRun</code> call will check that the caller has permissions to call the function, especially for checking cross-account permissions.</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>function_arn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the function to be invoked</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the function to be invoked. This can only be used for invocations within the calling account. To invoke a function in another account, use <em>function_arn</em> to specify the full ARN.</div></td></tr>
            <tr>
    <td>payload<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary in any form to be provided as input to the Lambda function.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>tail_log<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If <code>tail_log=true</code>, the result of the task will include the last 4 KB of the CloudWatch log for the function execution. Log tailing only works if you use synchronous invocation <code>wait=true</code>. This is usually used for development or testing Lambdas.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>version_qualifier<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>LATEST</td>
        <td><ul></ul></td>
        <td><div>Which version/alias of the function to run. This defaults to the <code>LATEST</code> revision, but can be set to any existing version or alias. See https;//docs.aws.amazon.com/lambda/latest/dg/versioning-aliases.html for details.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether to wait for the function results or not. If <em>wait</em> is false, the task will not return any results. To wait for the Lambda function to complete, set <code>wait=true</code> and the result will be available in the <em>output</em> key.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - execute_lambda:
        name: test-function
        # the payload is automatically serialized and sent to the function
        payload:
          foo: bar
          value: 8
      register: response
    
    # Test that you have sufficient permissions to execute a Lambda function in
    # another account
    - execute_lambda:
        function_arn: arn:aws:lambda:us-east-1:123456789012:function/some-function
        dry_run: true
    
    - execute_lambda:
        name: test-function
        payload:
          foo: bar
          value: 8
        wait: true
        tail_log: true
      register: response
      # the response will have a `logs` key that will contain a log (up to 4KB) of the function execution in Lambda.
    
    - execute_lambda: name=test-function version_qualifier=PRODUCTION

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
        <td> status </td>
        <td> C(StatusCode) of API call exit (200 for synchronous invokes, 202 for async) </td>
        <td align=center>  </td>
        <td align=center> int </td>
        <td align=center> 200 </td>
    </tr>
            <tr>
        <td> output </td>
        <td> Function output if wait=true and the function returns a value </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> { 'output': 'something' } </td>
    </tr>
            <tr>
        <td> logs </td>
        <td> The last 4KB of the function logs. Only provided if I(tail_log) is true </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Async invocation will always return an empty ``output`` key.
.. note:: Synchronous invocation may result in a function timeout, resulting in an empty ``output`` key.
.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

