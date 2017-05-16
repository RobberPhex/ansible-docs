.. _iam_policy:


iam_policy - Manage IAM policies for users, groups, and roles
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Allows uploading or removing IAM policies for IAM users, groups or roles.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * boto


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
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>iam_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of IAM resource you wish to target for policy actions. In other words, the user name, group name or role name.</div>        </td></tr>
                <tr><td>iam_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>user</li><li>group</li><li>role</li></ul></td>
        <td><div>Type of IAM resource</div>        </td></tr>
                <tr><td>policy_document<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to the properly json formatted policy file (mutually exclusive with <code>policy_json</code>)</div>        </td></tr>
                <tr><td>policy_json<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A properly json formatted policy as string (mutually exclusive with <code>policy_document</code>, see https://github.com/ansible/ansible/issues/7005#issuecomment-42894813 on how to use it properly)</div>        </td></tr>
                <tr><td>policy_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name label for the policy to create or remove.</div>        </td></tr>
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
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>skip_duplicates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td></td>
        <td><div>By default the module looks for any policies that match the document you pass in, if there is a match it will not make a new policy object with the same rules. You can override this by specifying false which would allow for two policy objects with different names but same rules.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to create or delete the IAM policy.</div>        </td></tr>
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

    # Create a policy with the name of 'Admin' to the group 'administrators'
    tasks:
    - name: Assign a policy called Admin to the administrators group
      iam_policy:
        iam_type: group
        iam_name: administrators
        policy_name: Admin
        state: present
        policy_document: admin_policy.json
    
    # Advanced example, create two new groups and add a READ-ONLY policy to both
    # groups.
    task:
    - name: Create Two Groups, Mario and Luigi
      iam:
        iam_type: group
        name: "{{ item }}"
        state: present
      with_items:
         - Mario
         - Luigi
      register: new_groups
    
    - name: Apply READ-ONLY policy to new groups that have been recently created
      iam_policy:
        iam_type: group
        iam_name: "{{ item.created_group.group_name }}"
        policy_name: "READ-ONLY"
        policy_document: readonlypolicy.json
        state: present
      with_items: "{{ new_groups.results }}"
    
    # Create a new S3 policy with prefix per user
    tasks:
    - name: Create S3 policy from template
      iam_policy:
        iam_type: user
        iam_name: "{{ item.user }}"
        policy_name: "s3_limited_access_{{ item.prefix }}"
        state: present
        policy_json: " {{ lookup( 'template', 's3_policy.json.j2') }} "
        with_items:
          - user: s3_user
            prefix: s3_user_prefix
    


Notes
-----

.. note::
    - Currently boto does not support the removal of Managed Policies, the module will not work removing/adding managed policies.
    - If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
    - Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
    - ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
