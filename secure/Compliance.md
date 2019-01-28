The Compliance module allows users to run tests on Docker and Kubernetes
environments against Center for Internet Security (CIS) standardized
benchmarks to determine the state of the environment. CIS provides
benchmarks, guidelines, and best practices for securing IT systems and
data.

For more information regarding CIS benchmarks, refer
to <a href="https://www.cisecurity.org/" class="external-link">https://www.cisecurity.org/</a>.

Contents
========

-   [The Module](#Compliance-TheModule)
    -   [The Results Page](#Compliance-TheResultsPage)
    -   [The Schedule Page](#Compliance-TheSchedulePage)
-   [Configure Tasks](#Compliance-ConfigureTasks)
    -   [Schedule a Task](#Compliance-ScheduleaTask)
    -   [Edit an Existing Task](#Compliance-EditanExistingTask)
    -   [Delete a Task](#Compliance-DeleteaTask)
-   [Review Task Results](#Compliance-ReviewTaskResults)
    -   [Search Test Results](#Compliance-SearchTestResults)
    -   [Kubernetes Benchmark Test
        Results](#Compliance-KubernetesBenchmarkTestResults)
    -   [Docker Benchmark Test
        Results](#Compliance-DockerBenchmarkTestResults)
    -   [Download Task Results](#Compliance-DownloadTaskResults)
-   [Dashboards and Metrics](#Compliance-DashboardsandMetrics)
    -   [Compliance Dashboards](#Compliance-ComplianceDashboards)
    -   [Compliance Metrics](#Compliance-ComplianceMetrics)

The Module
==========

The Results Page
----------------

The `Results` page displays a live list of task results run within the
environment. Each defined task is run on every node, and the results for
each node is a separate line item on the `Results` page. Users can
review individual task results, and navigate directly to the compliance
dashboards configured in Sysdig Monitor by clicking the links in the top
right corner of the page:

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

For more information on configuring compliance dashboards, refer to
the [Dashboards and
Metrics](#Compliance-**Compliance**-DashboardsandMetrics) section.

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/285540371.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

The list displays the following information:

-   The name of the task
-   The host MAC address
-   How long ago the task was run
-   The number of tests that passed.

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    For more information on task tests, refer to the [Review Task
    Results](https://sysdigdocs.atlassian.net/wiki/spaces/Secure/pages/282886237/Compliance#id-**Compliance**-ReviewTaskResults)
    section.

The Schedule Page
-----------------

The `Schedule` page provides a list of the configured tasks in Sysdig
Secure, and displays the scope, schedule, type of task they are, and
when the task will next run. Users can add new tasks, as well as edit or
delete existing tasks.

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/285474843.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

For detailed task configuration steps, refer to the [Configure
Tasks](#Compliance-Compliance-ConfigureTasks) section below.

Configure Tasks
===============

Schedule a Task
---------------

To schedule a new task:

1.  From the `Compliance` module, navigate to the `Schedule` page.
2.  Click the `Add Task` link:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/285376514.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>
3.  Configure the task name.  

4.  Set the type to `CIS Docker Bench` or `CIS Kubernetes Bench` as
    needed.
5.  Define how often the task will run.

6.  Define the scope.  

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    For more information about scopes, refer to the [Grouping, Scoping,
    and Segmenting
    Metrics](https://sysdigdocs.atlassian.net/wiki/spaces/Monitor/pages/215973889/Grouping%2C+Scoping%2C+and+Segmenting+Metrics)
    documentation.

    <span
    class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>
    To reset the scope of a new or existing task to the full
    environment, open the first drop-down list and select `Everywhere`.

7.  Click the `Save` button.

Edit an Existing Task
---------------------

To update/change an existing task:

1.  From the `Compliance` module, navigate to the `Schedule` page.
2.  Select the existing task from the list of configured tasks.
3.  Edit the task as necessary and click the `Save` button.

Delete a Task
-------------

To delete an existing task:

1.  From the `Compliance` module, navigate to the `Schedule` page.
2.  Click the `More Options` (three dots) icon for the relevant task:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/285507597.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" height="103" /></span>  
3.  Select `Delete task`.
4.  Click the `Yes` button to confirm, or the `No` button to revert the
    change.

Review Task Results
===================

Results from completed tasks can be reviewed from the `Results` page, by
clicking on an individual task from the list. Opening a task displays
the `Test Results` page for either Kubernetes or Docker (as
appropriate), and provides a detailed report as to how the node
performed against the benchmark tests.

The sections below provide screenshots of example benchmark results, and
a link to the specific CIS benchmark results document download page. For
more information about CIS practices, refer
to <a href="https://www.cisecurity.org/" class="external-link">https://www.cisecurity.org/</a>.

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

As shown in the Docker section below, some results have code blocks
beneath them. These provide detailed information that users can copy and
paste into support tickets should an issue arise, to assist the support
team in finding the issue quickly.

  

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

When a compliance test fails, an error log is displayed in place of the
task results.

Search Test Results
-------------------

The Results page can be searched/filtered using the search bar
functionality at the top of the page:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/318013525.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

Kubernetes Benchmark Test Results
---------------------------------

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/285474861.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

For the complete CIS Kubernetes Benchmark documentation, refer
to <a href="https://www.cisecurity.org/benchmark/kubernetes/" class="external-link">https://www.cisecurity.org/benchmark/kubernetes/</a>.

<span style="font-size: 20.0px;">Docker Benchmark Test Results</span>
---------------------------------------------------------------------

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/286720015.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" height="407" /></span>

<span
class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

For the complete CIS Docker Benchmark documentation, refer
to <a href="https://www.cisecurity.org/benchmark/docker/" class="external-link">https://www.cisecurity.org/benchmark/docker/</a>.

Download Task Results
---------------------

CIS compliance task results can be downloaded as a .CSV file:

1.  From the Compliance module, navigate to the `Results` page.
2.  Select the relevant task.
3.  Click the Download CSV button:  
    <span
    class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/315818053.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

Dashboards and Metrics
======================

Compliance Dashboards
---------------------

Sysdig provides two pre-built compliance dashboards as part of Sysdig
Monitor. These dashboards are called `Compliance (K8s)` and
`Compliance (Docker)`, and can be found by searching the list of
pre-built dashboards for the word "`Compliance`", or by scrolling to the
`Compliance` section of the list.

For information on building dashboards from scratch, or using the
pre-built dashboards, refer to the [Configure
Dashboards](https://sysdigdocs.atlassian.net/wiki/spaces/Monitor/pages/213516400/Configure+Dashboards) documentation.

The example dashboard below is a Docker compliance dashboard:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/286752769.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

The example dashboard below is a Kubernetes compliance dashboard:

<span
class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/282886237/286818305.png?width=600" class="confluence-embedded-image confluence-content-image-border" width="600" /></span>

Compliance Metrics
------------------

A number of compliance metrics for both Kubernetes and Docker are
available to view in Sysdig Monitor dashboards. These metrics are
documented in full in the Metrics Dictionary, and are available
here: [Compliance](https://sysdigdocs.atlassian.net/wiki/spaces/Monitor/pages/261980227/Compliance).
