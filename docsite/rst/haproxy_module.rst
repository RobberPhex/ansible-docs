.. _haproxy:


haproxy - Enable, disable, and set weights for HAProxy backend servers using socket commands.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Enable, disable, and set weights for HAProxy backend servers using socket commands.




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
    <td>backend<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>auto-detected</td>
        <td><ul></ul></td>
        <td><div>Name of the HAProxy backend pool.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the backend host to change.</div></td></tr>
            <tr>
    <td>shutdown_sessions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When disabling a server, immediately terminate all the sessions attached to the specified server. This can be used to terminate long-running sessions after a server is put into maintenance mode.</div></td></tr>
            <tr>
    <td>socket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/var/run/haproxy.sock</td>
        <td><ul></ul></td>
        <td><div>Path to the HAProxy socket file.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>Desired state of the provided backend host.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Wait until the server reports a status of 'UP' when `state=enabled`, or status of 'MAINT' when `state=disabled`.</div></td></tr>
            <tr>
    <td>wait_interval<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td><div>Number of seconds to wait between retries.</div></td></tr>
            <tr>
    <td>wait_retries<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>25</td>
        <td><ul></ul></td>
        <td><div>Number of times to check for status after changing the state.</div></td></tr>
            <tr>
    <td>weight<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The value passed in argument. If the value ends with the `%` sign, then the new weight will be relative to the initially configured weight. Relative weights are only permitted between 0 and 100% and absolute weights are permitted between 0 and 256.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # disable server in 'www' backend pool
    - haproxy: state=disabled host={{ inventory_hostname }} backend=www
    
    # disable server without backend pool name (apply to all available backend pool)
    - haproxy: state=disabled host={{ inventory_hostname }}
    
    # disable server, provide socket file
    - haproxy: state=disabled host={{ inventory_hostname }} socket=/var/run/haproxy.sock backend=www
    
    # disable server, provide socket file, wait until status reports in maintenance
    - haproxy: state=disabled host={{ inventory_hostname }} socket=/var/run/haproxy.sock backend=www wait=yes
    
    # disable backend server in 'www' backend pool and drop open sessions to it
    - haproxy: state=disabled host={{ inventory_hostname }} backend=www socket=/var/run/haproxy.sock shutdown_sessions=true
    
    # enable server in 'www' backend pool
    - haproxy: state=enabled host={{ inventory_hostname }} backend=www
    
    # enable server in 'www' backend pool wait until healthy
    - haproxy: state=enabled host={{ inventory_hostname }} backend=www wait=yes
    
    # enable server in 'www' backend pool wait until healthy. Retry 10 times with intervals of 5 seconds to retrieve the health
    - haproxy: state=enabled host={{ inventory_hostname }} backend=www wait=yes wait_retries=10 wait_interval=5
    
    # enable server in 'www' backend pool with change server(s) weight
    - haproxy: state=enabled host={{ inventory_hostname }} socket=/var/run/haproxy.sock weight=10 backend=www
    
    author: "Ravi Bhure (@ravibhure)"


Notes
-----

.. note:: Enable and disable commands are restricted and can only be issued on sockets configured for level 'admin'. For example, you can add the line 'stats socket /var/run/haproxy.sock level admin' to the general section of haproxy.cfg. See http://haproxy.1wt.eu/download/1.5/doc/configuration.txt.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

