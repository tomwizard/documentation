The Commands Audit module provides Sysdig Secure users with a searchable
and sortable audit trail of user commands executed within the
infrastructure.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

While policy events are inherently suspicious activity that warrant
investigation, commands are not themselves considered suspicious.

The Sysdig Agent examines all execve events. Information about commands
that meet the following criteria is saved by the Sysdig backend, and
made available for review as a command entry in the Commands Audit
module table:

-   A program was launched by a shell associated with a terminal (i.e.
    is related to a user-entered command).
-   The parent process was launched in a running container (i.e. the
    result of a `docker exec <container>` command).

<span
class="aui-icon aui-icon-small aui-iconfont-error confluence-information-macro-icon"></span>

<span style="color: rgb(23,43,77);">If an excessive volume of commands
occur in a given second, some commands may be excluded from the
information sent from the agent to the Sysdig backend.</span>

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261783611/261980237.png?width=867" class="confluence-embedded-image confluence-content-image-border" width="867" height="250" /></span>

The table below outlines the information displayed in the Command Audits
module:

| Data         | Description                                           |
|--------------|-------------------------------------------------------|
| Time         | The date and time the command was executed.           |
| Shell        | The terminal shell the command was executed in.       |
| Command Line | The full command executed, including flags/variables. |
| Scope        | The affected scope within the infrastructure.         |

Contents
========

-   [Review a Command](#CommandsAudit-ReviewaCommand)
-   [Filtering the Commands
    Table](#CommandsAudit-FilteringtheCommandsTable)
    -   [Groupings](#CommandsAudit-Groupings)
    -   [Time Navigation](#CommandsAudit-TimeNavigation)
    -   [Search Filters](#CommandsAudit-SearchFilters)

Review a Command
================

Individual commands can be reviewed by selecting the line item in the
Commands Audit module table. This opens the `Command Details` window:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261783611/269090817.png?width=500" class="confluence-embedded-image confluence-content-image-border" width="500" height="585" /></span>

The table below outlines the information displayed in the
`Command Details` window:

<table>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>When</td>
<td>The date and time the command was executed.</td>
</tr>
<tr class="even">
<td>Command</td>
<td><div class="content-wrapper">
<p>The command executed.</p>
</div></td>
</tr>
<tr class="odd">
<td>Full Command Line</td>
<td>The complete command, including all variables/options.</td>
</tr>
<tr class="even">
<td>Working Directory</td>
<td><div class="content-wrapper">
<p>The directory the command was executed in.</p>
</div></td>
</tr>
<tr class="odd">
<td>Scope</td>
<td>The entities within the infrastructure impacted by the command.</td>
</tr>
<tr class="even">
<td>Host</td>
<td>The hostname and MAC address of the host the command was executed on.</td>
</tr>
<tr class="odd">
<td>Container</td>
<td>The container ID, container name, and image that the command was executed on.</td>
</tr>
<tr class="even">
<td>Additional Details</td>
<td><div class="content-wrapper">
Detailed user/host information:<br />

<ul>
<li>The Process ID (PID) of the command.</li>
<li>The Parent Process ID (PPID) of the command.</li>
<li>The user ID of the user that executed the command.</li>
<li>The Shell ID.</li>
<li>The distance from the root of the process hierarchy.</li>
</ul>
</div></td>
</tr>
</tbody>
</table>

Filtering the Commands Table
============================

The Commands Audit module's table can be filtered to display only the
most relevant commands for a particular issue, or to provide greater
visibility of a more targeted scope within the infrastructure. There are
three ways to filter the table, which can be used in tandem to refine
the information presented.

Groupings
---------

<span style="color: rgb(9,30,66);">Groupings</span><span
style="color: rgb(51,51,51);"> are hierarchical organizations of labels,
allowing users to organize their infrastructure views in a logical
hierarchy. Users can switch between pre-configured groupings via the
`Browse By` menu, or configure custom groupings, and then dive deeper
into the infrastructure. For more information about groupings, refer to
the [Configure Groupings in Sysdig
Secure](Configure-Groupings-in-Sysdig-Secure_279740425.html)
documentation</span>

Time Navigation
---------------

<span style="color: rgb(9,30,66);">The time window navigation bar
provides users with quick links to common time windows, filtering the
table to only show commands run within that window. For more information
on time windows, refer to the [Time
Windows](https://sysdigdocs.atlassian.net/wiki/spaces/Monitor/pages/239337526/Time+Windows)
documentation.</span>

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

Sysdig Secure does not currently provide functionality to configure a
custom time window.

Search Filters
--------------

Search filters can be applied by either using the search bar directly,
or by adding pre-configured search strings via the Command Details
panel. The search bar example below displays only table items that
include `apt-get`:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261783611/269025305.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" height="143" /></span>

To use a pre-configured search string:

1.  From the `Commands Audit` module, select a command from the table to
    open the `Command Details` window.
2.  Add a filter by click the `Add` link beside one of the available
    options:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261783611/269254693.png?width=400" class="confluence-embedded-image confluence-content-image-border" width="400" /></span>

The example below shows the table filtered by the working directory:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261783611/269025313.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" height="201" /></span>

Pre-configured filters exist for the following information:

-   Command
-   Working Directory
-   Process ID
-   Parent Process ID
-   User ID
-   Shell ID
-   Shell Distance

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

Search filters can be deleted by either deleting the text in the search
bar, or clicking the `Remove` link beside the filter in the
`Command Details` window.
