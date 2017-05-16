.. _azure_rm_deployment:


azure_rm_deployment - Create or destroy Azure Resource Manager template deployments
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create or destroy Azure Resource Manager template deployments via the Azure SDK for Python. You can find some quick start templates in GitHub here https://github.com/azure/azure-quickstart-templates. For more information on Azue resource manager templates see https://azure.microsoft.com/en-us/documentation/articles/resource-group-template-deploy/.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * azure == 2.0.0rc5


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
    <td>ad_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Active Directory username. Use when authenticating with an Active Directory user rather than service principal.</div></td></tr>
            <tr>
    <td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client ID. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>deployment_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>incremental</td>
        <td><ul><li>complete</li><li>incremental</li></ul></td>
        <td><div>In incremental mode, resources are deployed without deleting existing resources that are not included in the template. In complete mode resources are deployed and existing resources in the resource group not included in the template are deleted.</div></td></tr>
            <tr>
    <td>deployment_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ansible-arm</td>
        <td><ul></ul></td>
        <td><div>The name of the deployment to be tracked in the resource group deployment history. Re-using a deployment name will overwrite the previous value in the resource group's deployment history.</div></td></tr>
            <tr>
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>westus</td>
        <td><ul></ul></td>
        <td><div>The geo-locations in which the resource group will be located.</div></td></tr>
            <tr>
    <td>parameters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash of all the required template variables for the deployment template. This parameter is mutually exclusive with 'parameters_link'. Either one of them is required if "state" parameter is "present".</div></td></tr>
            <tr>
    <td>parameters_link<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Uri of file containing the parameters body. This parameter is mutually exclusive with 'parameters'. Either one of them is required if "state" parameter is "present".</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Active Directory user password. Use when authenticating with an Active Directory user rather than service principal.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Security profile found in ~/.azure/credentials file.</div></td></tr>
            <tr>
    <td>resource_group_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The resource group name to use or create to host the deployed template</div></td></tr>
            <tr>
    <td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure client secret. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>If state is "present", template will be created. If state is "present" and if deployment exists, it will be updated. If state is "absent", stack will be removed.</div></td></tr>
            <tr>
    <td>subscription_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Your Azure subscription Id.</div></td></tr>
            <tr>
    <td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash containing the templates inline. This parameter is mutually exclusive with 'template_link'. Either one of them is required if "state" parameter is "present".</div></td></tr>
            <tr>
    <td>template_link<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Uri of file containing the template body. This parameter is mutually exclusive with 'template'. Either one of them is required if "state" parameter is "present".</div></td></tr>
            <tr>
    <td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Azure tenant ID. Use when authenticating with a Service Principal.</div></td></tr>
            <tr>
    <td>wait_for_deployment_completion<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to block until the deployment has completed.</div></td></tr>
            <tr>
    <td>wait_for_deployment_polling_period<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Time (in seconds) to wait between polls when waiting for deployment completion.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Destroy a template deployment
    - name: Destroy Azure Deploy
      azure_rm_deployment:
        state: absent
        subscription_id: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
        resource_group_name: dev-ops-cle
    
    # Create or update a template deployment based on uris using parameter and template links
    - name: Create Azure Deploy
      azure_rm_deployment:
        state: present
        resource_group_name: dev-ops-cle
        template_link: 'https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-vm-simple-linux/azuredeploy.json'
        parameters_link: 'https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-vm-simple-linux/azuredeploy.parameters.json'
    
    # Create or update a template deployment based on a uri to the template and parameters specified inline.
    # This deploys a VM with SSH support for a given public key, then stores the result in 'azure_vms'. The result is then
    # used to create a new host group. This host group is then used to wait for each instance to respond to the public IP SSH.
    ---
    - hosts: localhost
      connection: local
      gather_facts: no
      tasks:
        - name: Destroy Azure Deploy
          azure_rm_deployment:
            state: absent
            subscription_id: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
            resource_group_name: dev-ops-cle
    
        - name: Create Azure Deploy
          azure_rm_deployment:
            state: present
            subscription_id: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
            resource_group_name: dev-ops-cle
            parameters:
              newStorageAccountName:
                value: devopsclestorage1
              adminUsername:
                value: devopscle
              dnsNameForPublicIP:
                value: devopscleazure
              location:
                value: West US
              vmSize:
                value: Standard_A2
              vmName:
                value: ansibleSshVm
              sshKeyData:
                value: YOUR_SSH_PUBLIC_KEY
            template_link: 'https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/101-vm-sshkey/azuredeploy.json'
          register: azure
    
        - name: Add new instance to host group
          add_host: hostname={{ item['ips'][0].public_ip }} groupname=azure_vms
          with_items: azure.deployment.instances
    
        - hosts: azure_vms
          user: devopscle
          tasks:
            - name: Wait for SSH to come up
              wait_for: port=22 timeout=2000 state=started
            - name: echo the hostname of the vm
              shell: hostname
    
    # Deploy an Azure WebApp running a hello world'ish node app
    - name: Create Azure WebApp Deployment at http://devopscleweb.azurewebsites.net/hello.js
      azure_rm_deployment:
        state: present
        subscription_id: cbbdaed0-fea9-4693-bf0c-d446ac93c030
        resource_group_name: dev-ops-cle-webapp
        parameters:
          repoURL:
            value: 'https://github.com/devigned/az-roadshow-oss.git'
          siteName:
            value: devopscleweb
          hostingPlanName:
            value: someplan
          siteLocation:
            value: westus
          sku:
            value: Standard
        template_link: 'https://raw.githubusercontent.com/azure/azure-quickstart-templates/master/201-web-app-github-deploy/azuredeploy.json'
    
    # Create or update a template deployment based on an inline template and parameters
    - name: Create Azure Deploy
      azure_rm_deployment:
        state: present
        subscription_id: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
        resource_group_name: dev-ops-cle
    
        template:
          $schema: "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#"
          contentVersion: "1.0.0.0"
          parameters:
            newStorageAccountName:
              type: "string"
              metadata:
                description: "Unique DNS Name for the Storage Account where the Virtual Machine's disks will be placed."
            adminUsername:
              type: "string"
              metadata:
                description: "User name for the Virtual Machine."
            adminPassword:
              type: "securestring"
              metadata:
                description: "Password for the Virtual Machine."
            dnsNameForPublicIP:
              type: "string"
              metadata:
                description: "Unique DNS Name for the Public IP used to access the Virtual Machine."
            ubuntuOSVersion:
              type: "string"
              defaultValue: "14.04.2-LTS"
              allowedValues:
                - "12.04.5-LTS"
                - "14.04.2-LTS"
                - "15.04"
              metadata:
                description: "The Ubuntu version for the VM. This will pick a fully patched image of this given Ubuntu version. Allowed values: 12.04.5-LTS, 14.04.2-LTS, 15.04."
          variables:
            location: "West US"
            imagePublisher: "Canonical"
            imageOffer: "UbuntuServer"
            OSDiskName: "osdiskforlinuxsimple"
            nicName: "myVMNic"
            addressPrefix: "10.0.0.0/16"
            subnetName: "Subnet"
            subnetPrefix: "10.0.0.0/24"
            storageAccountType: "Standard_LRS"
            publicIPAddressName: "myPublicIP"
            publicIPAddressType: "Dynamic"
            vmStorageAccountContainerName: "vhds"
            vmName: "MyUbuntuVM"
            vmSize: "Standard_D1"
            virtualNetworkName: "MyVNET"
            vnetID: "[resourceId('Microsoft.Network/virtualNetworks',variables('virtualNetworkName'))]"
            subnetRef: "[concat(variables('vnetID'),'/subnets/',variables('subnetName'))]"
          resources:
            -
              type: "Microsoft.Storage/storageAccounts"
              name: "[parameters('newStorageAccountName')]"
              apiVersion: "2015-05-01-preview"
              location: "[variables('location')]"
              properties:
                accountType: "[variables('storageAccountType')]"
            -
              apiVersion: "2015-05-01-preview"
              type: "Microsoft.Network/publicIPAddresses"
              name: "[variables('publicIPAddressName')]"
              location: "[variables('location')]"
              properties:
                publicIPAllocationMethod: "[variables('publicIPAddressType')]"
                dnsSettings:
                  domainNameLabel: "[parameters('dnsNameForPublicIP')]"
            -
              type: "Microsoft.Network/virtualNetworks"
              apiVersion: "2015-05-01-preview"
              name: "[variables('virtualNetworkName')]"
              location: "[variables('location')]"
              properties:
                addressSpace:
                  addressPrefixes:
                    - "[variables('addressPrefix')]"
                subnets:
                  -
                    name: "[variables('subnetName')]"
                    properties:
                      addressPrefix: "[variables('subnetPrefix')]"
            -
              type: "Microsoft.Network/networkInterfaces"
              apiVersion: "2015-05-01-preview"
              name: "[variables('nicName')]"
              location: "[variables('location')]"
              dependsOn:
                - "[concat('Microsoft.Network/publicIPAddresses/', variables('publicIPAddressName'))]"
                - "[concat('Microsoft.Network/virtualNetworks/', variables('virtualNetworkName'))]"
              properties:
                ipConfigurations:
                  -
                    name: "ipconfig1"
                    properties:
                      privateIPAllocationMethod: "Dynamic"
                      publicIPAddress:
                        id: "[resourceId('Microsoft.Network/publicIPAddresses',variables('publicIPAddressName'))]"
                      subnet:
                        id: "[variables('subnetRef')]"
            -
              type: "Microsoft.Compute/virtualMachines"
              apiVersion: "2015-06-15"
              name: "[variables('vmName')]"
              location: "[variables('location')]"
              dependsOn:
                - "[concat('Microsoft.Storage/storageAccounts/', parameters('newStorageAccountName'))]"
                - "[concat('Microsoft.Network/networkInterfaces/', variables('nicName'))]"
              properties:
                hardwareProfile:
                  vmSize: "[variables('vmSize')]"
                osProfile:
                  computername: "[variables('vmName')]"
                  adminUsername: "[parameters('adminUsername')]"
                  adminPassword: "[parameters('adminPassword')]"
                storageProfile:
                  imageReference:
                    publisher: "[variables('imagePublisher')]"
                    offer: "[variables('imageOffer')]"
                    sku: "[parameters('ubuntuOSVersion')]"
                    version: "latest"
                  osDisk:
                    name: "osdisk"
                    vhd:
                      uri: "[concat('http://',parameters('newStorageAccountName'),'.blob.core.windows.net/',variables('vmStorageAccountContainerName'),'/',variables('OSDiskName'),'.vhd')]"
                    caching: "ReadWrite"
                    createOption: "FromImage"
                networkProfile:
                  networkInterfaces:
                    -
                      id: "[resourceId('Microsoft.Network/networkInterfaces',variables('nicName'))]"
                diagnosticsProfile:
                  bootDiagnostics:
                    enabled: "true"
                    storageUri: "[concat('http://',parameters('newStorageAccountName'),'.blob.core.windows.net')]"
        parameters:
          newStorageAccountName:
            value: devopsclestorage
          adminUsername:
            value: devopscle
          adminPassword:
            value: Password1!
          dnsNameForPublicIP:
            value: devopscleazure

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
        <td> deployment </td>
        <td> Deployment details </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'instances': {'type': 'list', 'description': 'Provides the public IP addresses for each VM instance.', 'returned': 'always'}, 'group_name': {'type': 'string', 'description': 'Name of the resource group', 'returned': 'always'}, 'id': {'type': 'string', 'description': 'The Azure ID of the deployment', 'returned': 'always'}, 'name': {'type': 'string', 'description': 'Name of the deployment', 'returned': 'always'}, 'outputs': {'type': 'dict', 'description': 'Dictionary of outputs received from the deployment', 'returned': 'always'}} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: For authentication with Azure you can pass parameters, set environment variables or use a profile stored in ~/.azure/credentials. Authentication is possible using a service principal or Active Directory user. To authenticate via service principal pass subscription_id, client_id, secret and tenant or set set environment variables AZURE_SUBSCRIPTION_ID, AZURE_CLIENT_ID, AZURE_SECRET and AZURE_TENANT.
.. note:: To Authentication via Active Directory user pass ad_user and password, or set AZURE_AD_USER and AZURE_PASSWORD in the environment.
.. note:: Alternatively, credentials can be stored in ~/.azure/credentials. This is an ini file containing a [default] section and the following keys: subscription_id, client_id, secret and tenant or subscription_id, ad_user and password. It is also possible to add additional profiles. Specify the profile by passing profile or setting AZURE_PROFILE in the environment.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

