The Policies module displays a comprehensive list of all policies
defined for the Sysdig Secure environment. Policies are a collection of
rules that define the boundaries of expected behavior for the
environment, and set in place actions to be taken should behavior
outside those boundaries occurs. Through this module, policies, and the
underlying rules that define them, can be added, edited, or removed.

Rules can be defined to whitelist or blacklist specific commands and
processes, container images, network connections, read/write
permissions, and system calls. In addition, advanced/custom rules can be
written, using the Falco rules syntax. Falco is a behavioral activity
monitoring tool, designed to detect abnormal behavior in applications
and containers.

For more information about Falco, refer to the
<a href="https://github.com/falcosecurity/falco/wiki/About-Falco" class="external-link">Falco documentation</a>.

Contents
========

-   [Navigate the Policies Module](#Policies-NavigatethePoliciesModule)
    -   [The Policies Tab](#Policies-ThePoliciesTab)
        -   [Configure the Policies
            List](#Policies-ConfigurethePoliciesList)
    -   [The Rules Editor Tab](#Policies-TheRulesEditorTab)
-   [Configure Policies](#Policies-ConfigurePolicies)
    -   [Create a Policy](#Policies-CreateaPolicy)
    -   [Edit Existing Policies](#Policies-EditExistingPolicies)
    -   [Duplicate an Existing
        Policy](#Policies-DuplicateanExistingPolicy)
    -   [Delete Existing Policies](#Policies-DeleteExistingPolicies)
-   [Advanced Rules](#Policies-AdvancedRules)
    -   [Update the Default Falco Rules (On-Premises Environments
        Only)](#Policies-UpdatetheDefaultFalcoRules(On-PremisesEnvironmentsOnly))

Navigate the Policies Module
============================

The Policies Tab
----------------

The **`Policies`** tab displays the list of currently configured
policies. These policies are listed in order of priority, and policies
are validated in priority order, from top to bottom, until a terminating
action (for example, a syscall is blacklisted, or a container is
stopped) occurs.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

The default priority is oldest → newest policy, based on date of
creation. Policy priority can be configured in the `Edit Policy` panel.

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/277413992.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" height="489" /></span>

The main policy list displays the following information:

<table>
<thead>
<tr class="header">
<th>Policy Information</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Severity</td>
<td><p>The configured severity of the policy. The severity reflects the risk and impact to the entities impacted if the policy is triggered:</p>
<ul>
<li>A yellow circle signifies a low-severity policy.</li>
<li>An orange circle signifies a medium-severity policy.</li>
<li>A red circle signifies a high-severity policy.</li>
<li>A grey circle signifies a disabled policy.</li>
</ul></td>
</tr>
<tr class="even">
<td>Policy Name</td>
<td>The name of the policy.</td>
</tr>
<tr class="odd">
<td>Scope</td>
<td>The entities impacted by the policy.</td>
</tr>
<tr class="even">
<td>Notification Channels</td>
<td>The types of notification channels configured for the policy. This is represented by one or more notification channel related icons.</td>
</tr>
<tr class="odd">
<td>Actions</td>
<td>The actions the policy should trigger. This is represented by a Stop or Pause icon, or left blank.</td>
</tr>
<tr class="even">
<td>Captures</td>
<td>Whether a capture file should be created. This is represented by the Captures (recording tape) icon.</td>
</tr>
</tbody>
</table>

Selecting a policy from the list opens a side panel, where the policy
can be reviewed in detail, and configured if necessary. For more
information, and examples, refer to the [Configure
Policies](https://sysdigdocs.atlassian.net/wiki/spaces/Secure/pages/261685292/Policies#Policies-ConfigurePolicies)
section below.

### Configure the Policies List

The policy list can be filtered and sorted to better show the policies
users need to review.

To filter the policies list:

1.  From the `Policies` module, open the `Severity` drop-down list:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/277446766.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" /></span>
2.  Check/uncheck the relevant severity types. The example below only
    displays `Low` severity policies:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/277381207.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" /></span>

To sort the policies list:

1.  From the `Policies` module, open the `Sort By` drop-down list:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/277348512.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" /></span>
2.  Select the preferred way to group/sort the policies. The example
    below groups the policies by severity:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/277643372.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" /></span>

The Rules Editor Tab
--------------------

The `Rules Editor` tab displays the default and custom Falco rules
currently configured for the environment.

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/277545097.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

The `Default Rules` panel is read-only for SaaS customers, and updated
with each release. On-premises customers need to update the default
rules manually. For more information, refer to the [Advanced
Rules](https://sysdigdocs.atlassian.net/wiki/spaces/Secure/pages/261685292/Policies#Policies-AdvancedRules)
section.

For more information on writing Falco rules, refer to the
<a href="https://github.com/draios/falco/wiki/Falco-Rules" class="external-link">Falco Rules</a>
documentation.

Configure Policies
==================

The creating/editing policies process can be broken into two main parts:
defining the general properties of the policy (for example, the scope
and notification channels), and defining the rules that form the policy
framework.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

New Falco rules must be written **before** they can be added to a
new/edited policy. For more information on creating rules with Sysdig
Falco, refer to the
<a href="https://github.com/draios/falco/wiki/Falco-Rules" class="external-link">Falco Rules</a>
documentation.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

Notification channels must be created before they can be added to a
new/edited policy. For more information on configuring notification
channels, refer to the [Notifications
Management](https://sysdigdocs.atlassian.net/wiki/spaces/Platform/pages/206503956/Notifications+Management)
documentation.

Create a Policy
---------------

To create a new policy:

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

Steps three → eight in the following process are optional, as a policy
does not require every type of rule to be configured. However, at least
one rule type must be configured for the policy to be created.

1.  From the `Policies` module, click the `Add Policy` button.
2.  Configure the policy's general properties:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/274726944.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>
    1.  Define a meaningful policy name.
    2.  **Optional:** Define an accurate policy description to increase
        user accessibility.
    3.  Set the policy severity to `High` (red), `Medium` (orange), or
        `Low` (Yellow)

        <span
        class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
        Policy severity is subjective, and is used to group policies
        within a Sysdig Secure instance. 

    4.  Toggle the `Enabled` switch as necessary.
    5.  Define the policy priority within the infrastructure.

        <span
        class="aui-icon aui-icon-small aui-iconfont-error confluence-information-macro-icon"></span>
        Policy priority is critical to the policy workflow. Sysdig
        recommends reviewing policy priorities whenever a new policy is
        created, to ensure policies are triggered in the correct order.

    6.  Define the policy scope within the infrastructure, and whether
        the policy applies to hosts and/or containers.
    7.  Define the actions that should occur when the policy is
        triggered:
        1.  Set the container action to `Nothing` (no change will occur,
            but a event notification will be sent), `Stop` (the
            container will be killed), or `Pause` (the container will be
            paused for review).
        2.  **Optional:** Check the Captures checkbox to enable capture
            creation, and define the time before and after the event the
            capture file should record.

            <span
            class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
            For more information about capture files, refer to
            the [Captures](Captures_258375681.html) documentation.

    8.  Add the notification channels the policy should use if
        triggered.

        <span
        class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
        For more information on configuring notification channels, refer
        to the [Notifications
        Management](https://sysdigdocs.atlassian.net/wiki/spaces/Platform/pages/206503956/Notifications+Management)
        documentation.

3.  **Optional:** Navigate to the `Processes` tab:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/275283969.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

    <span
    class="aui-icon aui-icon-small aui-iconfont-error confluence-information-macro-icon"></span>
    Process names must match exactly. Wildcards and partial matches are
    not supported.

    1.  Define a comma-separated list of processes to whitelist.
    2.  Define a comma-separated list of processes to blacklist.
    3.  Select either `Evaluate next policy`, `Whitelist`, or
        `Blacklist`, for all processes not explicitly listed in steps a
        and b.

4.  **Optional:** Navigate to the **`Containers`** tab:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/275415044.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    Container image names can be expressed in the following formats:

    -   `name`
    -   `name:tag`
    -   `name:tag@digest`
    -   `host:port/name:tag@digest`
    -   `host/name:tag@digest`

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    Wildcards and partial matches are not supported. For example, the
    string `mys` cannot be used to match all `mysql` containers.
    However, the string `mysql` will match both `mysql:latest` and
    `mysql:1.2.4.`

    1.  Define a comma-separated list of container images to whitelist.
    2.  Define a comma-separated list of container images to blacklist.
    3.  Select either `Evaluate next policy`, `Whitelist`, or
        `Blacklist`, for all container images not explicitly listed in
        steps a and b.

5.  **Optional:** Navigate to the `Network` tab:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/275251219.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    Sysdig only considers listening ports for policy configuration. Port
    matching is only done once, when the listen occurs, and not for any
    additional activity.

    1.  Define whether inbound/outbound connections can be initiated
        within the configured scope.
    2.  Define the TCP ports that can be/cannot be used for listening.
    3.  Define the UDP ports that can be/cannot be used for listening.
    4.  Select either `Evaluate next policy`, `Whitelist`, or
        `Blacklist`, for all container images not explicitly listed in
        steps b and c.

6.  **Optional:** Navigate to the `File System` tab:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/275218442.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" height="427" /></span>

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    Policy violations for file system rules are evaluated when common
    system calls for file/directory opening, creation, renaming, and
    removing are successfully executed.

    The following system calls are currently supported:

    -   `open/openat`
    -   `mkdir/mkdirat`
    -   `rmdir`
    -   `rename/renameat`
    -   `unlink/unlinkat`

    1.  Define the read/write operations that should be
        whitelisted/blacklisted for the configured scope.
    2.  Define the read only operations that should be
        whitelisted/blacklisted for the configured scope.
    3.  Select either `Evaluate next policy`, `Whitelist`, or
        `Blacklist`, for all operations not defined in steps a and b.

7.  **Optional:** Navigate to the `Syscalls` tab:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/275382282.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

    <span
    class="aui-icon aui-icon-small aui-iconfont-error confluence-information-macro-icon"></span>
    System call names must match exactly. Wildcards and partial matches
    are not supported.

    1.  Define a comma-separated list of system calls to whitelist.
    2.  Define a comma-separated list of system calls to blacklist.
    3.  Select either `Evaluate next policy`, `Whitelist`, or
        `Blacklist`, for all system calls not explicitly listed in steps
        a and b.

8.  **Optional:** Navigate to the `Falco` tab:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/275447827.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>  
    1.  Open the `Falco Rules` drop-down list.
    2.  Select the Falco rule for the policy to use.

        <span
        class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
        New Falco rules must be written **before** they can be added to
        a new/edited policy. For more information on creating rules with
        Sysdig Falco, refer to the
        <a href="https://github.com/draios/falco/wiki/Falco-Rules" class="external-link">Falco Rules</a>
        documentation.

9.  **Optional:** Repeat steps one → eight to create additional policies
    before saving.
10. Click the `Apply Changes` button to save the changes, or the
    `Discard / Discard All` button to revert all changes.

Edit Existing Policies
----------------------

To edit an existing policy:

1.  From the `Policies` module, select the relevant policy.
2.  Edit the policy as necessary.
3.  **Optional:** Repeat steps one and two for each additional policy
    that needs to be edited.
4.  Click the `Apply Changes` button to save the changes, or the
    `Discard / Discard All` button to revert all changes.

Duplicate an Existing Policy
----------------------------

Policies can be duplicated to speed up the policy creation process. This
is useful when multiple policies have similar scopes, rules, or other
configuration options. To duplicate an existing policy:

1.  From the `Policies` module, select the relevant policy.
2.  Click the `Copy Policy` (pages) icon, either in the Policies list,
    or in the `Edit Policy` window:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/271876128.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" /></span>
3.  Edit the new policy.
4.  **Optional:** Repeat steps one, two, and three for each additional
    policy that needs to be duplicated.
5.  Click the `Apply Changes` button to save the changes, or the
    `Discard / Discard All` button to revert all changes.

Delete Existing Policies
------------------------

Policies can be deleted via the `Edit Policy` window. To delete a
policy/multiple policies:

1.  From the `Policies` module, select the relevant policy.
2.  Click the `Delete` (trash can) icon in the `Edit Policy` window:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/272039979.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>
3.  **Optional:** Repeat steps one and two to tag multiple policies for
    deletion:

    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/272203806.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" height="210" /></span>

4.  Click the `Apply Changes` button to save the changes, the `Revert`
    (left arrow) icon to revert the changes to a single policy, or the
    `Discard / Discard All` button to revert all changes:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261685292/272007219.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

Advanced Rules
==============

In Sysdig Secure, advanced/complex rules can be created for policies
using the Falco Rules Engine. Sysdig provides a number of default Falco
rules already configured. These rules can be modified or overwritten,
allowing for the creation of detailed policies.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

For more information on writing Falco rules, refer to
the <a href="https://github.com/draios/falco/wiki/Falco-Rules" class="external-link">Falco Rules</a>
documentation.

Update the Default Falco Rules (On-Premises Environments Only)
--------------------------------------------------------------

New Falco rules are regularly added to the default Falco rules list by
the Sysdig Engineering Team. On-premises environments need to be updated
manually to add the new rules.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

The `Default Rules` panel is read-only for SaaS customers, and updated
with each release.

To update the default Falco rules:

1.  In a web browser, navigate
    to <a href="https://raw.githubusercontent.com/draios/falco/dev/rules/falco_rules.yaml" class="external-link">https://raw.githubusercontent.com/draios/falco/dev/rules/falco_rules.yaml</a>.
2.  Copy the Falco Rules file content.
3.  In a web browser, navigate
    to <a href="https://secure.sysdig.com" class="external-link">https://secure.sysdig.com</a>.
4.  Open the `Policies` module.
5.  Navigate to the `Rules Editor` tab.
6.  Replace the default rules with the latest version, and click the
    `Save` button.

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    Updating the default rules will not override existing custom rules.
