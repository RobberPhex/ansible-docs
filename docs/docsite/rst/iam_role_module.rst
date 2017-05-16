.. _iam_role:


iam_role - Manage AWS IAM roles
+++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage AWS IAM roles


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3
  * botocore
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
                <tr><td>assume_role_policy_document<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The trust relationship policy document that grants an entity permission to assume the role.  This parameter is required when state: present.</div>        </td></tr>
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
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>managed_policy<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A list of managed policy ARNs (can't use friendly names due to AWS API limitation) to attach to the role. To embed an inline policy, use <span class='module'>iam_policy</span>. To remove existing policies, use an empty list item.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the role to create.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td></td>
        <td><div>The path to the role. For more information about paths, see <a href='http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html'>http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html</a>.</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or remove the IAM role</div>        </td></tr>
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
    
    # Create a role
    - iam_role:
        name: mynewrole
        assume_role_policy_document: "{{ lookup('file','policy.json') }}"
        state: present
    
    # Create a role and attach a managed policy called "PowerUserAccess"
    - iam_role:
        name: mynewrole
        assume_role_policy_document: "{{ lookup('file','policy.json') }}"
        state: present
        managed_policy:
          - arn:aws:iam::aws:policy/PowerUserAccess
    
    # Keep the role created above but remove all managed policies
    - iam_role:
        name: mynewrole
        assume_role_policy_document: "{{ lookup('file','policy.json') }}"
        state: present
        managed_policy:
          -
    
    # Delete the role
    - iam_role:
        name: mynewrole
        assume_role_policy_document: "{{ lookup('file','policy.json') }}"
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
        <td> attached_policies </td>
        <td> a list of dicts containing the name and ARN of the managed IAM policies attached to the role </td>
        <td align=center>  </td>
        <td align=center> list </td>
        <td align=center> [{'policy_arn': 'arn:aws:iam::aws:policy/PowerUserAccess', 'policy_name': 'PowerUserAccess'}] </td>
    </tr>
            <tr>
        <td> assume_role_policy_document </td>
        <td> the policy that grants an entity permission to assume the role </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> {'version': '2012-10-17', 'statement': [{'action': 'sts:AssumeRole', 'principal': {'service': 'ec2.amazonaws.com'}, 'effect': 'Allow', 'sid': ''}]} </td>
    </tr>
            <tr>
        <td> role_name </td>
        <td> the friendly name that identifies the role </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> myrole </td>
    </tr>
            <tr>
        <td> create_date </td>
        <td> the date and time, in ISO 8601 date-time format, when the role was created </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 2016-08-14T04:36:28+00:00 </td>
    </tr>
            <tr>
        <td> path </td>
        <td> the path to the role </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> / </td>
    </tr>
            <tr>
        <td> arn </td>
        <td> the Amazon Resource Name (ARN) specifying the role </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> arn:aws:iam::1234567890:role/mynewrole </td>
    </tr>
            <tr>
        <td> role_id </td>
        <td> the stable and unique string identifying the role </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> ABCDEFF4EZ4ABCDEFV4ZC </td>
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

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
