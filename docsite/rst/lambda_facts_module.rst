.. _lambda_facts:


lambda_facts - Gathers AWS Lambda function details as Ansible facts
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Gathers various details related to Lambda functions, including aliases, versions and event source mappings. Use module :ref:`lambda <lambda>` to manage the lambda function itself, :ref:`lambda_alias <lambda_alias>` to manage function aliases and :ref:`lambda_event <lambda_event>` to manage lambda event source mappings.


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
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>event_source_arn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>For query type 'mappings', this is the Amazon Resource Name (ARN) of the Amazon Kinesis or DynamoDB stream.</div></td></tr>
            <tr>
    <td>function_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the lambda function for which facts are requested.</div></br>
        <div style="font-size: small;">aliases: function, name<div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>query<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>all</td>
        <td><ul><li>aliases</li><li>all</li><li>config</li><li>mappings</li><li>policy</li><li>versions</li></ul></td>
        <td><div>Specifies the resource type for which to gather facts.  Leave blank to retrieve all facts.</div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # Simple example of listing all info for a function
    - name: List all for a specific function
      lambda_facts:
        query: all
        function_name: myFunction
      register: my_function_details
    # List all versions of a function
    - name: List function versions
      lambda_facts:
        query: versions
        function_name: myFunction
      register: my_function_versions
    # List all lambda function versions
    - name: List all function
      lambda_facts:
        query: all
        max_items: 20
    - name: show Lambda facts
      debug: var=lambda_facts

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
        <td> lambda_facts.function </td>
        <td> lambda function list </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> lambda_facts.function.TheName </td>
        <td> lambda function information, including event, mapping, and version information </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> lambda_facts </td>
        <td> lambda facts </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

