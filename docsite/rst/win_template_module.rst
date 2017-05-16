.. _win_template:


win_template - Templates a file out to a remote server.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Templates are processed by the Jinja2 templating language (http://jinja.pocoo.org/docs/) - documentation on the template formatting can be found in the Template Designer Documentation (http://jinja.pocoo.org/docs/templates/).
Six additional variables can be used in templates: ``ansible_managed`` (configurable via the ``defaults`` section of ``ansible.cfg``) contains a string which can be used to describe the template name, host, modification time of the template file and the owner uid, ``template_host`` contains the node name of the template's machine, ``template_uid`` the owner, ``template_path`` the absolute path of the template, ``template_fullpath`` is the absolute path of the template, and ``template_run_date`` is the date that the template was rendered. Note that including a string that uses a date in the template will result in the template being marked 'changed' each time.




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
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Location to render the template to on the remote machine.</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path of a Jinja2 formatted template on the local server. This can be a relative or absolute path.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Playbook Example  (win_template can only be run inside a playbook)
    - win_template: src=/mytemplates/file.conf.j2 dest=C:\temp\file.conf
    
    


Notes
-----

.. note:: templates are loaded with ``trim_blocks=True``.
.. note:: By default, windows line endings are not created in the generated file.
.. note:: In order to ensure windows line endings are in the generated file, add the following header as the first line of your template: ``#jinja2: newline_sequence:'\r\n'`` and ensure each line of the template ends with \\r\\n
.. note:: Beware fetching files from windows machines when creating templates because certain tools, such as Powershell ISE,  and regedit's export facility add a Byte Order Mark as the first character of the file, which can cause tracebacks.
.. note:: Use "od -cx" to examine your templates for Byte Order Marks.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

