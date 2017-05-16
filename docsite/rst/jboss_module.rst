.. _jboss:


jboss - deploy applications to JBoss
++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Deploy applications to JBoss standalone using the filesystem




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
    <td>deploy_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/var/lib/jbossas/standalone/deployments</td>
        <td><ul></ul></td>
        <td><div>The location in the filesystem where the deployment scanner listens</div></td></tr>
            <tr>
    <td>deployment<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the deployment</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The remote path of the application ear or war to deploy</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the application should be deployed or undeployed</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Deploy a hello world application
    - jboss: src=/tmp/hello-1.0-SNAPSHOT.war deployment=hello.war state=present
    # Update the hello world application
    - jboss: src=/tmp/hello-1.1-SNAPSHOT.war deployment=hello.war state=present
    # Undeploy the hello world application
    - jboss: deployment=hello.war state=absent


Notes
-----

.. note:: The JBoss standalone deployment-scanner has to be enabled in standalone.xml
.. note:: Ensure no identically named application is deployed through the JBoss CLI


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

