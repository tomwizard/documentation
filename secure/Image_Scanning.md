Sysdig Secure provides image scanning functionality, allowing users to
identify known vulnerabilities and misconfigurations, prevent vulnerable
images from being deployed, and report on the risk level of images
actively running in the environment. Images can be scanned and analyzed
either manually, or as part of the build pipeline via a Jenkins plugin.

<span
class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>

The Image Scanning feature is available for Sysdig Secure SaaS.  

As part of the analysis, artifacts are created and stored. These
artifacts include:

-   Official OS packages
-   Unofficial packages
-   Configuration files
-   Artifacts such as NPM modules, PiP, GEM, and Java Archives
-   Secrets or sensitive data
-   Available updates for vulnerabilities.

Once the image analysis is complete, the contents are evaluated against
multiple vulnerability databases (shown in the image below), and a
user-defined policy list, to determine if the image meets or violates
configured policies.

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/256507943/259194938.png?width=684" class="confluence-embedded-image confluence-content-image-border" width="684" height="203" /></span>

<span style="font-size: 24.0px;">Contents</span>

-   [Configure the Build
    Environment](#ImageScanning-ConfiguretheBuildEnvironment)
    -   [Configure the Anchore
        CLI](#ImageScanning-ConfiguretheAnchoreCLI)
    -   [Configure the Jenkins
        Plugin](#ImageScanning-ConfiguretheJenkinsPlugin)
-   [Registries](#ImageScanning-Registries)
    -   [Configure Registry
        Credentials](#ImageScanning-ConfigureRegistryCredentials)
        -   [Configure a Docker Hub Private
            Registry](#ImageScanning-ConfigureaDockerHubPrivateRegistry)
        -   [Configure a Google Container
            Registry](#ImageScanning-ConfigureaGoogleContainerRegistry)
        -   [Configure an Amazon Elastic Container Registry (AWS
            ECR)](#ImageScanning-ConfigureanAmazonElasticContainerRegistry(AWSECR))
        -   [Configure a Gitlab
            Registry](#ImageScanning-ConfigureaGitlabRegistry)
        -   [Configure a Microsoft Azure Container
            Registry](#ImageScanning-ConfigureaMicrosoftAzureContainerRegistry)
        -   [Configure a Quay
            Registry](#ImageScanning-ConfigureaQuayRegistry)
-   [Scan Images](#ImageScanning-ScanImages)
    -   [Manually Scan an Image](#ImageScanning-ManuallyScananImage)
    -   [Configure Alerts to Automatically Scan
        Images](#ImageScanning-ConfigureAlertstoAutomaticallyScanImages)
-   [Scanning Policies](#ImageScanning-ScanningPolicies)
    -   [Create a New Policy](#ImageScanning-CreateaNewPolicy)
    -   [Edit an Existing Policy](#ImageScanning-EditanExistingPolicy)
    -   [Delete an Existing
        Policy](#ImageScanning-DeleteanExistingPolicy)
-   [Alerts](#ImageScanning-secure-alertsAlerts)
    -   [Create an Alert](#ImageScanning-CreateanAlert)
    -   [Edit an Existing Alert](#ImageScanning-EditanExistingAlert)
    -   [Delete an Existing Alert](#ImageScanning-DeleteanExistingAlert)

Configure the Build Environment
===============================

Several steps are required to configure the build environment for image
scanning.

Configure the Anchore CLI
-------------------------

Sysdig Secure uses the Anchore open-source engine to perform image
analysis. Users can use the `anchore-cli` with Sysdig Secure for easier
registry integrations, command line reporting, and advanced repository
subscription capabilities.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

The Anchore CLI is available for download from
GitHub: <a href="https://github.com/anchore/anchore-cli" class="external-link">https://github.com/anchore/anchore-cli</a>.
For installation steps, refer to the README file.

Several environment variables should be configured as part of the
installation and setup process, depending on whether you are using an
on-premises or SaaS environment:

-   For on-premises environments:

    ``` syntaxhighlighter-pre
    export ANCHORE_CLI_URL=https://ONPREM_SYSDIG_HOST/api/scanning/v1/anchore
    export ANCHORE_CLI_USER=SYSDIG_SECURE_API_TOKEN
    export ANCHORE_CLI_PASS=
    export ANCHORE_CLI_SSL_VERIFY=n
    ```

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    Replace the `ONPREM_SYSDIG_HOST` variable with the host used to
    reach the Sysdig UI, and the `SYSDIG_SECURE_API_TOKEN` variable with
    API token found in the Sysdig Secure UI.

-   For SaaS environments:

    ``` syntaxhighlighter-pre
    export ANCHORE_CLI_URL=https://secure.sysdig.com/api/scanning/v1/anchore
    export ANCHORE_CLI_USER=SYSDIG_SECURE_API_TOKEN
    export ANCHORE_CLI_PASS=
    ```

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    Replace the `SYSDIG_SECURE_API_TOKEN` variable with API token found
    in the Sysdig Secure UI.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

Ensure the `ANCHORE_CLI_PASS` value remains empty for both on-premises
and SaaS environments.

Listed below are several useful CLI commands.

**Add an image to the Anchore Engine**

``` syntaxhighlighter-pre
user@host:~$ anchore-cli image add docker.io/library/debian:latest
```

**List images analyzed by the Anchore Engine**

``` syntaxhighlighter-pre
user@host:~$ anchore-cli image list
```

**Get a specific image and see when its status goes to analyzed**

``` syntaxhighlighter-pre
user@host:~$ anchore-cli image get docker.io/library/debian:latest
```

**Perform a vulnerability scan on an image**

``` syntaxhighlighter-pre
user@host:~$ anchore-cli image vuln docker.io/library/debian:latest os
```

<span style="font-size: 20.0px;">Configure the Jenkins Plugin</span>
--------------------------------------------------------------------

Sysdig provides users with a Jenkins plugin to allow them to integrate
the image scanning functionality with their existing build process. For
more information on configuring the plugin, refer to the
<a href="https://wiki.jenkins.io/display/JENKINS/Sysdig+Secure+Jenkins+Plugin" class="external-link">Sysdig Secure Jenkins Plugin</a>
documentation.

Registries
==========

Configure Registry Credentials
------------------------------

For registries that require login credentials, the relevant
username/password needs to be added to the Sysdig Secure interface. To
add new registry credentials:

From the `Image Scanning` module, navigate to the `Registry Credentials`
tab.

Click the `Add Registry` button.  
<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/256507943/258867201.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" height="171" /></span>

Define the path to the registry.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

Only the site name is needed for the path (for example, `docker.io`. The
leading `http(s)://` and trailing path should not be included.

Input the relevant username and password for the registry, and click the
`Save Registry` button.

### Configure a Docker Hub Private Registry

<span style="color: rgb(23,43,77);">For Docker Hub private registries,
the path should be `docker.io`.</span>

### Configure a Google Container Registry

Sysdig recommends using JSON keys rather than the short-lived access
tokens, when configuring a Google Container Registry (GCR). JSON key
files are long-lived, and are tightly scoped to individual projects and
resources.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

For more information on JSON credentials, refer to the
<a href="https://cloud.google.com/container-registry/docs/advanced-authentication#using_a_json_key_file" class="external-link">Google Container Registry Advanced Authentication</a>
documentation.

Once a JSON key file has been created with permissions to read from the
container registry, the registry should be added with the username
`_json_key`, and using the contents of the key file as the password. The
example below, the JSON key is stored in a file called key.json:

``` syntaxhighlighter-pre
user@host:~$ anchore-cli registry add us.gcr.io _json_key "$(cat key.json)" --skip-validate
```

### Configure an Amazon Elastic Container Registry (AWS ECR)

The scanning engine uses AWS access keys and secret access keys to
generate authentication tokens, in order to access the Amazon ECR
registry.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

Generated authentication tokens typically expire within 12 hours.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

Sysdig recommends using the `anchore-cli` to pass the AWS access key
credentials to Sysdig Secure when configuring ECR access. For
information on configuring the `anchore-cli`, refer to the [Configure
the Anchore
CLI](https://sysdigdocs.atlassian.net/wiki/spaces/Secure/pages/256507943/Image+Scanning#ImageScanning-ConfiguretheAnchoreCLI)
documentation above.

To generate authentication tokens for Amazon ECR:

In a terminal, run the following `anchore-cli` command. The variables in
the command should be replaced by the AWS access key ID and key,
respectively:

``` syntaxhighlighter-pre
user@host:~$ anchore-cli registry add 1234567890.dkr.ecr.us-east-1.amazonaws.com AWS_ACCESS_KEY_ID AWS_SECRET_ACCESS_KEY --registry-type=awsecr
```

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

For more information on configuring AWS ECR, refer to the
<a href="https://anchore.freshdesk.com/support/solutions/articles/36000047969-working-with-amazon-ecr-registry-credentials" class="external-link">Amazon ECR registry credentials</a>
documentation.

### Configure a Gitlab Registry

Sysdig recommends using the following command when configuring a Gitlab
registry:

``` syntaxhighlighter-pre
user@host:~$ anchore-cli registry add --skip-validate -- gitlab-registry.COMPANY_NAME.com MY_USER --MY_SECRET
```

### Configure a Microsoft Azure Container Registry

There are two different ways to configure access to a Microsoft Azure
Container Registry

**1. Admin Account**

Username: The username in the 'az acr credentials show --name
&lt;registry name&gt;' output

Password: The password or password2 value from the 'az acr credentials
show' command result

**2. Service Principal**

Username: The service principal app id

Password: The service principal password

### Configure a Quay Registry

When using a Quay robot account, the required username will
be `ORG_NAME+USER_NAME`.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

Standard Quay user accounts do not need the `ORG_NAME+` part of the
username value.

Scan Images
===========

Manually Scan an Image
----------------------

When a new image is added to a running environment, it may need to be
scanned manually. This can be done from either the `Runtime` tab, or the
`Repositories` tab.

To manually scan an image from the `Runtime` tab:

From the `Image Scanning` module, navigate to the `Repositories` tab.

Select an image from the list of unscanned images.  
<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/256507943/258965505.png?width=800" class="confluence-embedded-image confluence-content-image-border" width="800" /></span>

Click the `Scan Now` button to scan the image.

To manually scan an image from the `Repositories` tab:

From the `Image Scanning` module, navigate to the `Repositories` tab.

Click the `Scan Image` button.  
<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/256507943/258867206.png?width=800" class="confluence-embedded-image confluence-content-image-border" width="800" height="108" /></span>

Define the path to the image, and click the `Scan` button.  
<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/256507943/259031044.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" height="164" /></span>

Configure Alerts to Automatically Scan Images
---------------------------------------------

Sysdig Secure alerts can be configured to automatically trigger image
scanning if an unscanned image is found, by setting the
**`Unscanned Image`** trigger drop-down menu to `Scan Image`:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/256507943/305364996.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

For more information regarding configuring Alerts, refer to
the [Alerts](#ImageScanning-secure-alerts) section below.

Scanning Policies
=================

Image scanning policies define the scenarios in which the build process
may be stopped, or admins may be alerted to potential risks within
container images. Each scanning policy is made up of a number of rules,
triggers, and actions. The policy evaluation results are displayed on
both the `Runtime` and `Repositories` tabs, allowing users to drill down
into policies from a live image, or to select an image from within a
repository to view the results.

Create a New Policy
-------------------

To create a new scanning policy:

From the `Image Scanning` module, navigate to the `Scanning Policies`
tab.

Click the `Add Policy` button.

Define a name for the new policy.

**Optional:** Provide a description for the policy, for ease of review.

Add a rule:

Open the `Rules` drop-down menu, and select the desired trigger. The
example below uses `High Severity CVE`.  
<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/256507943/259129345.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

Define the parameters for the trigger with the trigger specific text
boxes and drop-down menus. The example below has several rules and
trigger configurations.  
<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/256507943/259162113.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

**Optional:** Repeat step 5 to add additional rules as necessary.

Click the `Save Policy` button.

Edit an Existing Policy
-----------------------

To edit an existing scanning policy:

From the `Image Scanning` module, navigate to the `Scanning Policies`
tab.

Select the desired policy from the list.

Edit the policy rules as required, and click the `Save Policy` button.

Delete an Existing Policy
-------------------------

To delete an existing scanning policy:

From the `Image Scanning` module, navigate to the `Scanning Policies`
tab.

Select the desired policy from the list.

Click the `Delete` (trash can) icon.

Select the `Yes` option to confirm the change.

<span id="ImageScanning-secure-alerts" class="confluence-anchor-link"></span>Alerts
===================================================================================

Image scanning alerts, like all Sysdig alerts, can be configured to
notify users when an issue in the infrastructure arises. However, image
scanning alerts focus on two issues: when an image has failed a scanning
policy evaluation, or an unscanned image has been added to the
environment.

Create an Alert
---------------

To create a new alert:

From the `Image Scanning` module, navigate to the `Alerts` tab.

Click the `Add Alert` button.  
<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/256507943/259129378.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

Define the name of the alert.

**Optional:** Provide a description for the alert, for ease of review.

Open the `Scope` drop-down menu, and select the desired alert scope.

Select the desired triggers.

Click the `+ Add Channel `notification channels link to add a new
notification channel.

Edit an Existing Alert
----------------------

To edit an existing alert:

From the `Image Scanning` module, navigate to the `Alerts` tab.

Select the desired alert from the list.

Edit the alert trigger, scope, and notification channels as necessary,
and click the `Save Alert` button.

Delete an Existing Alert
------------------------

To delete an existing alert:

From the `Image Scanning `module, navigate to the `Alerts` tab.

Select the desired policy from the list.

Click the `Delete` (trash can) icon.

Select the `Yes` option to confirm the change.
