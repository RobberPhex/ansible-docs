.. _pushover:


pushover - Send notifications via u(https://pushover.net)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Send notifications via pushover, to subscriber list of devices, and email addresses. Requires pushover app on devices.




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
    <td>app_token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>P</div><div>u</div><div>s</div><div>h</div><div>o</div><div>v</div><div>e</div><div>r</div><div> </div><div>i</div><div>s</div><div>s</div><div>u</div><div>e</div><div>d</div><div> </div><div>t</div><div>o</div><div>k</div><div>e</div><div>n</div><div> </div><div>i</div><div>d</div><div>e</div><div>n</div><div>t</div><div>i</div><div>f</div><div>y</div><div>i</div><div>n</div><div>g</div><div> </div><div>y</div><div>o</div><div>u</div><div>r</div><div> </div><div>p</div><div>u</div><div>s</div><div>h</div><div>o</div><div>v</div><div>e</div><div>r</div><div> </div><div>a</div><div>p</div><div>p</div><div>.</div></td></tr>
            <tr>
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>W</div><div>h</div><div>a</div><div>t</div><div> </div><div>m</div><div>e</div><div>s</div><div>s</div><div>a</div><div>g</div><div>e</div><div> </div><div>y</div><div>o</div><div>u</div><div> </div><div>w</div><div>i</div><div>s</div><div>h</div><div> </div><div>t</div><div>o</div><div> </div><div>s</div><div>e</div><div>n</div><div>d</div><div>.</div></td></tr>
            <tr>
    <td>pri<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>M</div><div>e</div><div>s</div><div>s</div><div>a</div><div>g</div><div>e</div><div> </div><div>p</div><div>r</div><div>i</div><div>o</div><div>r</div><div>i</div><div>t</div><div>y</div><div> </div><div>(</div><div>s</div><div>e</div><div>e</div><div> </div><div>u</div><div>(</div><div>h</div><div>t</div><div>t</div><div>p</div><div>s</div><div>:</div><div>/</div><div>/</div><div>p</div><div>u</div><div>s</div><div>h</div><div>o</div><div>v</div><div>e</div><div>r</div><div>.</div><div>n</div><div>e</div><div>t</div><div>)</div><div> </div><div>f</div><div>o</div><div>r</div><div> </div><div>d</div><div>e</div><div>t</div><div>a</div><div>i</div><div>l</div><div>s</div><div>.</div><div>)</div></td></tr>
            <tr>
    <td>user_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>P</div><div>u</div><div>s</div><div>h</div><div>o</div><div>v</div><div>e</div><div>r</div><div> </div><div>i</div><div>s</div><div>s</div><div>u</div><div>e</div><div>d</div><div> </div><div>a</div><div>u</div><div>t</div><div>h</div><div>e</div><div>n</div><div>t</div><div>i</div><div>c</div><div>a</div><div>t</div><div>i</div><div>o</div><div>n</div><div> </div><div>k</div><div>e</div><div>y</div><div> </div><div>f</div><div>o</div><div>r</div><div> </div><div>y</div><div>o</div><div>u</div><div>r</div><div> </div><div>u</div><div>s</div><div>e</div><div>r</div><div>.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - local_action: pushover msg="{{inventory_hostname}} has exploded in flames,
      It is now time to panic" app_token=wxfdksl user_key=baa5fe97f2c5ab3ca8f0bb59


Notes
-----

.. note:: You will require a pushover.net account to use this module. But no account is required to receive messages.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

