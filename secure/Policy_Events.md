The Policy Events module displays a complete list of all events that
have occurred within the infrastructure during a defined timeline. The
module provides users with an overview of the entire infrastructure, as
well as the functionality to deep dive into specific components,
identify false positives, and configure policies to optimize
performance.

Contents
========

-   [Navigate the Policy Events
    Module](#PolicyEvents-NavigatethePolicyEventsModule)
    -   [List View](#PolicyEvents-ListView)
    -   [Event Details](#PolicyEvents-EventDetails)
    -   [Topology View](#PolicyEvents-TopologyView)
-   [Filter Policy Events](#PolicyEvents-FilterPolicyEvents)
    -   [Groupings](#PolicyEvents-Groupings)
    -   [Time Navigation](#PolicyEvents-TimeNavigation)
    -   [Search Filters](#PolicyEvents-SearchFilters)

Navigate the Policy Events Module
=================================

List View
---------

The list view provides a comprehensive list of all events within the
grouping/timeline, in chronological order:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261947484/279150627.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

If multiple events occur at the same time, the dot will contain the
number of events:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261947484/279019548.png?width=400" class="confluence-embedded-image confluence-content-image-border" width="400" height="387" /></span>

This view presents events in reverse chronological order, with the most
recent event listed at the top. The following information is displayed:

<table style="width:100%;">
<colgroup>
<col style="width: 6%" />
<col style="width: 93%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Severity</td>
<td><div class="content-wrapper">
<p>The severity of the event based on the policies triggered.</p>
<ul>
<li>A yellow dot signifies a low-severity event.</li>
<li>An orange dot signifies a medium-severity event.</li>
<li>A red dot signifies a high-severity event.</li>
</ul>
</div></td>
</tr>
<tr class="even">
<td>Rule Type</td>
<td><p>The type of rule violated by the event. Each rule type is represented by a periodic table style identifier:</p>
<ul>
<li>Pr: Processes</li>
<li>Co: Containers</li>
<li>Ne: Network</li>
<li>Fi: File System</li>
<li>Sy: Syscall</li>
<li>Fa: Falco</li>
</ul></td>
</tr>
<tr class="odd">
<td>Policy List</td>
<td><p>The policy or policies triggered by the event/s. Each policy is listed in bold text.</p></td>
</tr>
<tr class="even">
<td>Entity</td>
<td><div class="content-wrapper">
<p>The entity the event originated from. The entities will reflect the current <code>Browse By</code> menu selection, and any selected entry in the drill-down menu.</p>
<div class="confluence-information-macro confluence-information-macro-note">
<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
<p>If multiple entities are impacted, a notation will appear stating <code>X entities involved</code>, where <code>X</code> represents the number of impacted entities.</p>
</div>
</div>
</div></td>
</tr>
<tr class="odd">
<td>Action(s) taken</td>
<td><p>The action(s) taken in response to the event. Each action is represented by an icon:</p>
<ul>
<li>A pause symbol indicates the container was paused. The container remains paused until a user executes a <code>docker unpause</code> operation.</li>
<li>A stop symbol indicated the container was stopped and did not resume operation.</li>
<li>A tape symbol indicates a capture was recorded for the event.</li>
</ul></td>
</tr>
</tbody>
</table>

Event Details
-------------

Selecting an event opens the **`Policy Event Details`** panel, which
displays a detailed summary of the event, the location it occurred, and
the policies that were violated:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261947484/279740498.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

The following information is displayed:

<table style="width:100%;">
<colgroup>
<col style="width: 8%" />
<col style="width: 91%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>When</td>
<td>The date and time the event(s) occurred.</td>
</tr>
<tr class="even">
<td>Related Resources</td>
<td><p>Additional information about the event, including:</p>
<ul>
<li>The <strong><code>View Captures</code></strong> button opens the <strong><code>Captures</code></strong> tab, and provides access to the capture recorded for the event.</li>
<li>The <code>View Commands</code> button opens the <code>Commands History</code> tab, and provides access to the command(s) that triggered the event.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Severity</td>
<td><p>The severity of the event(s) based on the policies triggered.</p>
<ul>
<li>A yellow bar signifies low-severity.</li>
<li>An orange bar signifies medium-severity.</li>
<li>A red bar signifies high-severity.</li>
</ul></td>
</tr>
<tr class="even">
<td>Triggered Policy</td>
<td><div class="content-wrapper">
<p>The policies that triggered the event(s). The link opens the <code>Policies</code> tab and expands the selected policy.</p>
<div class="confluence-information-macro confluence-information-macro-note">
<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
<p>Add/remove filter links next to each policy will add/remove that policy to the search bar.</p>
</div>
</div>
</div></td>
</tr>
<tr class="odd">
<td>Triggered Rule Type</td>
<td><p>The type of rule violated by the event. Each rule type is represented by a periodic table style identifier:</p>
<ul>
<li>Pr: Processes</li>
<li>Co: Containers</li>
<li>Ne: Network</li>
<li>Fi: File System</li>
<li>Sy: Syscall</li>
<li>Fa: Falco</li>
</ul></td>
</tr>
<tr class="even">
<td>Scope</td>
<td><div class="content-wrapper">
<p>The scope of the event within the infrastructure.</p>
<div class="confluence-information-macro confluence-information-macro-note">
<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>
<div class="confluence-information-macro-body">
<p>The entities listed, and the order they appear, will vary based on the grouping selected in the <code>Browse By</code> menu. For more information, refer to the <a href="https://sysdigdocs.atlassian.net/wiki/spaces/Secure/pages/3768655/Getting+Started#GettingStarted-BrowsetheInfrastructure">Browse the Infrastructure</a> section of the Sysdig Secure documentation.</p>
</div>
</div>
</div></td>
</tr>
<tr class="odd">
<td>Host</td>
<td>The hostname and MAC address of the host where the event occurred.</td>
</tr>
<tr class="even">
<td>Container</td>
<td>The ID, name, and image of the container where the event occurred.</td>
</tr>
<tr class="odd">
<td>Actions</td>
<td><p>The action(s) taken in response to the event(s). Each action is represented by an icon:</p>
<ul>
<li>A pause symbol indicates the container/s were paused. When it's paused, it remains paused until a user does a "docker unpause" operation.</li>
<li>A stop symbol indicated the container/s were stopped and did not resume operation.</li>
<li>A tape symbol indicates a capture was recorded for the event.</li>
</ul></td>
</tr>
<tr class="even">
<td>Summary</td>
<td>Detailed information regarding the event.</td>
</tr>
</tbody>
</table>

Topology View
-------------

The topology view provides an overview of all events, broken down
visually to show their network dependencies across the various hosts,
containers, and services, based on the configured grouping/timeline:

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

For more information on configuring groupings and time intervals, refer
to the Filter Policy Events section.

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261947484/279216143.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" height="333" /></span>

Each node can be drilled-down into, to find the exact events requiring
review, by zooming in, and selecting the `Expand` (plus) icon in the top
left corner of the node:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261947484/279216151.gif?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

Filter Policy Events
====================

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

Search filters can be applied by using the search bar. The event numbers
alongside the groupings in the `Browse By` menu will be updated to
reflect the number of events that meet the search criteria. The search
bar example below displays only `Write below rpm database` events:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/261947484/279707650.png?width=1000" class="confluence-embedded-image confluence-content-image-border" width="1000" /></span>

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

The topology view is not impacted by the search function.
