Sysdig capture files contain system calls and other OS events that can be analyzed with either the open-source `sysdig` or `csysdig` (curses-based) utilities, and are displayed in the Captures module.

The Captures module contains a table listing the capture file name, the host it was retrieved from, the time frame, and the size of the capture. When the capture file status is uploaded, the file has been successfully transmitted from the Sysdig agent to the storage bucket, and is available for download and analysis.

This section covers how to create capture files in Sysdig Secure.

# Contents

-   [Configure Capture Files](#Captures-ConfigureCaptureFiles)
    -   [Store Capture Files](#Captures-StoreCaptureFiles)
    -   [Create a Capture File](#Captures-CreateaCaptureFile)
    -   [Delete a Capture File](#Captures-DeleteaCaptureFile)
-   [Review Capture Files](#Captures-ReviewCaptureFiles)
    -   [Review the Capture Event in the Policy Events Module](#Captures-ReviewtheCaptureEventinthePolicyEventsModule)
    -   [Review the Capture File with Sysdig Inspect](#Captures-ReviewtheCaptureFilewithSysdigInspect)
    -   [Download a Capture File](#Captures-DownloadaCaptureFile)

# Configure Capture Files

## Store Capture Files

Sysdig capture files are stored in Sysdig's AWS S3 storage (for SaaS environments), or in the Cassandra DB (for on-premises environments) by default. To configure a custom S3 storage bucket, refer to the [Configure a Custom S3 Capture
Bucket](https://sysdigdocs.atlassian.net/wiki/spaces/Platform/pages/206569555) documentation.

## Create a Capture File

Capture files can be created in Sysdig Secure either by configuring them as part of a policy, or by manually creating them from the `Captures` module.

<span class="aui-icon aui-icon-small aui-iconfont-info confluence-information-macro-icon"></span>

For more information on creating a capture as part of a policy, refer to the Policies module documentation.

To manually create a capture file:

1.  From the `Captures` module, click the `Take Capture` button to open the capture creation window.  
    <span class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/258375681/271286309.png?width=846" class="confluence-embedded-image confluence-content-image-border" width="846" height="250" /></span>
2.  Define the name of the capture.
3.  Configure the host and container the capture file should record system calls from.
4.  Define the duration of the capture. The maximum length is 300 seconds (five minutes).
5.  Click the `Start` button.

The Sysdig agent will be signaled to start a capture, and send back the resulting trace file. The file will then be displayed in the `Captures` module.

## Delete a Capture File

1.  From the `Captures` module, select the capture file to be deleted.
2.  Click the `Delete` (trash can) icon: <span class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/258375681/271351914.png?width=800" class="confluence-embedded-image confluence-content-image-border" width="800" /></span>
3.  Click the `Yes` (tick) icon to confirm deleting the capture, or the `No` (cross) icon to cancel.

# Review Capture Files

## Review the Capture Event in the Policy Events Module

To review the event that caused the capture file's creation:

1.  From the `Captures` module, select the capture file to be deleted.
2.  Click the `View Policy Event` (list) icon: <span class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/258375681/271319103.png?width=800" class="confluence-embedded-image confluence-content-image-border" width="800" height="98" /></span>

Sysdig Secure will navigate to the `Policy Events` module, and display the exact event that caused the capture file.

## Review the Capture File with Sysdig Inspect

To review the capture file in Sysdig Inspect:

1.  From the `Captures` module, select the capture file to be deleted.
2.  Click the Inspect (Sysdig logo) icon to open Sysdig Inspect in a new browser tab: <span class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/258375681/271286326.png?width=800" class="confluence-embedded-image confluence-content-image-border" width="800" /></span>

## Download a Capture File

To download a capture file:

1.  From the `Captures` module, select the target capture file.
2.  Click the `Download` (down arrow) icon to download the capture file. <span class="confluence-embedded-file-wrapper confluence-embedded-manual-size"><img src="assets/images/258375681/271482983.png?width=800" class="confluence-embedded-image confluence-content-image-border" width="800" /></span>  

The capture file will now be downloaded to the local machine.
