.. _github_hooks:


github_hooks - Manages github service hooks.
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Adds service hooks and removes service hooks that have an error status.




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
    <td>action<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>cleanall</li></ul></td>
        <td><div>This tells the githooks module what you want it to do.</div></td></tr>
            <tr>
    <td>content_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>json</td>
        <td><ul><li>json</li><li>form</li></ul></td>
        <td><div>Content type to use for requests made to the webhook</div></td></tr>
            <tr>
    <td>hookurl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When creating a new hook, this is the url that you want github to post to. It is only required when creating a new hook.</div></td></tr>
            <tr>
    <td>oauthkey<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The oauth key provided by github. It can be found/generated on github under "Edit Your Profile" &gt;&gt; "Applications" &gt;&gt; "Personal Access Tokens"</div></td></tr>
            <tr>
    <td>repo<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>This is the API url for the repository you want to manage hooks for. It should be in the form of: https://api.github.com/repos/user:/repo:. Note this is different than the normal repo url.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Github username.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates for the target repo will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example creating a new service hook. It ignores duplicates.
    - github_hooks: action=create hookurl=http://11.111.111.111:2222 user={{ gituser }} oauthkey={{ oauthkey }} repo=https://api.github.com/repos/pcgentry/Github-Auto-Deploy
    
    # Cleaning all hooks for this repo that had an error on the last update. Since this works for all hooks in a repo it is probably best that this would be called from a handler.
    - local_action: github_hooks action=cleanall user={{ gituser }} oauthkey={{ oauthkey }} repo={{ repo }}




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

