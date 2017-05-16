.. _lambda_alias:


lambda_alias - Creates, updates or deletes AWS Lambda function aliases.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows the management of AWS Lambda functions aliases via the Ansible framework.  It is idempotent and supports "Check" mode.    Use module :ref:`lambda <lambda>` to manage the lambda function itself and :ref:`lambda_event <lambda_event>` to manage event source mappings.


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
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A short, user-defined function alias description.</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>function_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the function alias.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the function alias.</div></br>
        <div style="font-size: small;">aliases: alias_name<div></td></tr>
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
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Describes the desired state.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Version associated with the Lambda function alias. A value of 0 (or omitted parameter) sets the alias to the $LATEST version.</div></br>
        <div style="font-size: small;">aliases: function_version<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # Simple example to create a lambda function and publish a version
    - hosts: localhost
      gather_facts: no
      vars:
        state: present
        project_folder: /path/to/deployment/package
        deployment_package: lambda.zip
        account: 123456789012
        production_version: 5
      tasks:
      - name: AWS Lambda Function
        lambda:
          state: "{{ state | default('present') }}"
          name: myLambdaFunction
          publish: True
          description: lambda function description
          code_s3_bucket: package-bucket
          code_s3_key: "lambda/{{ deployment_package }}"
          local_path: "{{ project_folder }}/{{ deployment_package }}"
          runtime: python2.7
          timeout: 5
          handler: lambda.handler
          memory_size: 128
          role: "arn:aws:iam::{{ account }}:role/API2LambdaExecRole"
    
      - name: show results
        debug: var=lambda_facts
    
    # The following will set the Dev alias to the latest version ($LATEST) since version is omitted (or = 0)
      - name: "alias 'Dev' for function {{ lambda_facts.FunctionName }} "
        lambda_alias:
          state: "{{ state | default('present') }}"
          function_name: "{{ lambda_facts.FunctionName }}"
          name: Dev
          description: Development is $LATEST version
    
    # The QA alias will only be created when a new version is published (i.e. not = '$LATEST')
      - name: "alias 'QA' for function {{ lambda_facts.FunctionName }} "
        lambda_alias:
          state: "{{ state | default('present') }}"
          function_name: "{{ lambda_facts.FunctionName }}"
          name: QA
          version: "{{ lambda_facts.Version }}"
          description: "QA is version {{ lambda_facts.Version }}"
        when: lambda_facts.Version != "$LATEST"
    
    # The Prod alias will have a fixed version based on a variable
      - name: "alias 'Prod' for function {{ lambda_facts.FunctionName }} "
        lambda_alias:
          state: "{{ state | default('present') }}"
          function_name: "{{ lambda_facts.FunctionName }}"
          name: Prod
          version: "{{ production_version }}"
          description: "Production is version {{ production_version }}"

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
        <td> alias_arn </td>
        <td> Full ARN of the function, including the alias </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> arn:aws:lambda:us-west-2:123456789012:function:myFunction:dev </td>
    </tr>
            <tr>
        <td> function_version </td>
        <td> The qualifier that the alias refers to </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> $LATEST </td>
    </tr>
            <tr>
        <td> description </td>
        <td> A short description of the alias </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> The development stage for my hot new app </td>
    </tr>
            <tr>
        <td> name </td>
        <td> The name of the alias assigned </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> dev </td>
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

