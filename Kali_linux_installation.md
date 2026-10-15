## INSTALLATION GUIDE

## VMware Workstation Pro and Kali Linux Virtual Lab Environment

A standardized procedure for preparing a Windows host, installing VMware Workstation Pro,

and deploying Kali Linux as a virtual machine.

| Document Type | Installation Guide |
| --- | --- |
| Version | 1.0 |
| Status | Baseline / Reference |
| Platform | Windows host with VMware Workstation Pro |
| Target Environment | Kali Linux virtual machine for cybersecurity lab activities |


## 1. Document Control

| Version | Date | Author/Owner | Change Description |
| --- | --- | --- | --- |
| 1.0 | 08-Oct-2026 | Technical Documentation | Initial installation guide |

## 2. Purpose

This guide provides a structured procedure for preparing a Windows system, installing VMware Workstation Pro, and downloading, configuring, and validating a Kali Linux virtual machine. The resulting environment can be used for cybersecurity learning, testing, ethical hacking practice, penetration testing, and network security analysis.

## 3. Scope

This guide covers host-system verification, VMware Workstation Pro installation, Kali Linux virtual-machine deployment, virtual-machine upgrade, Internet connectivity validation, snapshot creation and restoration, and safe shutdown of the Kali Linux virtual machine.

## 4. Tools and Software

- Windows

- VMware Workstation Pro

- Kali Linux

- 7-Zip

## 5. Prerequisites

- Windows system available for the lab.

- VMware Workstation Pro available for installation.

- System virtualization technology enabled.

- Minimum 4 CPU cores and 8 logical processors.

- Minimum 8 GB RAM; 16 GB or higher is recommended.

- SSD storage.

- At least 120 GB of free space on an internal C: or D: drive for the complete setup.

- Internet connectivity for downloading the required software and validating the Kali Linux network connection.


## 6. Installation Procedure

Follow the tasks in sequence. Complete each verification point before proceeding to the next task.

## Part 1: System Preparation and Requirement Verification

### Task 1: Verify System Requirements

Objective: Ensure that the host system has sufficient CPU, virtualization support, memory, and storage for the virtual lab.

#### 1.1 Open Task Manager.

Purpose: In the Windows Search box, type “Task Manager” and select Open.

#### 1.2 Open the Performance view.

Purpose: Select Performance to view CPU, memory, and disk information.

#### 1.3 Verify CPU specifications.

Purpose: Select CPU and confirm a minimum of 4 cores and 8 logical processors.

#### 1.4 Verify virtualization.

Purpose: Confirm that virtualization technology is enabled. If it is disabled, enable it before continuing.

#### 1.5 Verify memory.

Purpose: Select Memory and confirm at least 8 GB RAM; 16 GB or higher is recommended.

#### 1.6 Verify disk type.

Purpose: Select Disk and confirm that the system uses SSD storage.

### Task 2: Verify Available Disk Space

Objective: Confirm that sufficient internal storage is available for VMware Workstation Pro and the virtual machine.

#### 2.1 Open File Explorer.

Purpose: In the Windows Search box, type “File Explorer” and select Open.

#### 2.2 Open This PC.

Purpose: Select This PC from the navigation pane.

## 2.3 Check free space.

Purpose: Confirm that at least 120 GB of free space is available on the internal C: or D: drive.

## Part 2: VMware Workstation Pro Installation

### Task 3: Download VMware Workstation Pro

Objective: Obtain the VMware Workstation Pro installation package.


### 3.1 Search for the VMware Workstation Pro download.

Purpose: In the browser search bar, search for “Download VMware 17 Pro”.

### 3.2 Open the download result.

Purpose: Select the VMware Workstation Pro download result used by the source procedure.

### 3.3 Locate the Windows download.

Purpose: On the download page, locate the Windows Workstation download option.

### 3.4 Download the installer.

Purpose: Select the applicable Workstation Windows package and wait for the download to complete.

### Task 4: Install and Configure VMware Workstation Pro

Objective: Install VMware Workstation Pro on the Windows host.

#### 4.1 Open File Explorer and the Downloads directory.

Purpose: Locate the downloaded VMware installer.

#### 4.2 Start the installer.

Purpose: Double-click the VMware Workstation installer.

#### 4.3 Proceed through the setup wizard.

Purpose: Select Next as prompted.

#### 4.4 Accept the license agreement.

Purpose: Select the option to accept the terms of the License Agreement and continue.

#### 4.5 Continue with the installation.

Purpose: Use the default or required setup options presented by the installer.

#### 4.6 Select the installation option.

Purpose: Proceed to the Install step.

#### 4.7 Complete installation.

Purpose: Allow the installer to finish and select Finish.

#### 4.8 Launch VMware Workstation Pro.

Purpose: Double-click VMware Workstation and confirm that the main interface opens.

## Part 3: Kali Linux Virtual Machine Installation

### Task 5: Download and Prepare Kali Linux

Objective: Download the Kali Linux VMware virtual-machine package and prepare it for import.

#### 5.1 Open the Kali Linux download page.

Purpose: Search for “Download Kali Linux”, select Get Kali, and then select Virtual Machines.


#### 5.2 Select the VMware download.

Purpose: Select the Download option under the VMware section.

#### 5.3 Verify the download.

Purpose: Open File Explorer and confirm that the Kali Linux package is present in the Downloads directory.

#### 5.4 Install 7-Zip.

Purpose: Download 7-Zip from its official website, run the installer, select Install, and then select Close.

#### 5.5 Extract the Kali Linux package.

Purpose: Right-click the downloaded Kali Linux VMware package, select Show more options, select 7- Zip, and then select Extract files.

#### 5.6 Select the VM destination.

Purpose: Choose an internal drive with sufficient free space. The source procedure uses D:\VM\Kali Linux when C: does not have enough space.

#### 5.7 Complete extraction.

Purpose: Select OK and wait for the extraction process to finish.

### Task 6: Open the Kali Linux VM in VMware

Objective: Import the extracted Kali Linux virtual machine into VMware Workstation Pro.

#### 6.1 Open VMware Workstation.

Purpose: Double-click the VMware Workstation icon.

#### 6.2 Open an existing VM.

Purpose: Select File, then Open.

#### 6.3 Navigate to the VM folder.

Purpose: Open the VM folder and then open the Kali Linux folder.

#### 6.4 Select the VM configuration.

Purpose: Double-click the Kali Linux VMware configuration file.

#### 6.5 Confirm the VM.

Purpose: Select Kali Linux and click Open. The Kali virtual machine should now appear in VMware.

### Task 7: Upgrade the Virtual Machine

Objective: Upgrade the virtual machine configuration for compatibility and improved operation.

#### 7.1 Start the VM upgrade process.

Purpose: Select Upgrade this virtual machine.

#### 7.2 Continue.

Purpose: Select Next.


#### 7.3 Select the target hardware compatibility.

Purpose: From the available options, select Workstation 17.5 or later.

#### 7.4 Complete the upgrade.

Purpose: Select Next, choose the option to apply the upgrade after the virtual machine, select Next, then select Finish.

###3 7.5 Close the upgrade workflow.

Purpose: Select Close.

## Part 4: Validation and Recovery Configuration

### Task 8: Verify Internet Connectivity

Objective: Confirm that the Kali Linux VM starts successfully and has network connectivity.

#### 8.1 Power on the virtual machine.

Purpose: Select Power on this Virtual Machine.

#### 8.2 Confirm startup prompts.

Purpose: Select OK if a startup prompt appears.

#### 8.3 Log in to Kali Linux.

Purpose: Use the credentials configured for the Kali Linux image. The source procedure identifies the default credentials for its image as username “kali” and password “kali”.

#### 8.4 Open a terminal.

Purpose: Launch the Terminal application in Kali Linux.

#### 8.5 Check the IP address.

Purpose: Run `ip a` and verify that a network interface has an assigned IP address. The source example shows 192.168.191.128; your address may be different.

#### 8.6 Test Internet connectivity.

Purpose: Run `ping -c 4 google.com` and verify that responses are received.

### Task 9: Create a VM Snapshot

Objective: Preserve a known working state of the Kali Linux VM so that it can be restored after testing or configuration changes.

#### 9.1 Open the VM menu.

Purpose: Select VM.

#### 9.2 Open Snapshot.

Purpose: Select Snapshot.

#### 9.3 Create a snapshot.

Purpose: Select Take Snapshot.


#### 9.4 Name the snapshot.

Purpose: Enter a meaningful snapshot name, then select Take Snapshot.

#### 9.5 Verify completion.

Purpose: Confirm that the snapshot appears in the snapshot view.

### Task 10: Restore a Snapshot

Objective: Restore the virtual machine to a previously saved state.

#### 10.1 Open the VM menu.

Purpose: Select VM.

#### 10.2 Open Snapshot.

Purpose: Select Snapshot.

#### 10.3 Select the required snapshot.

Purpose: Select Revert to snapshot and choose the required snapshot.

#### 10.4 Confirm the restore.

Purpose: Select Yes when prompted.

### Task 11: Shut Down Kali Linux

Objective: Safely shut down the operating system to prevent data loss and maintain system stability.

#### 11.1 Open the logout/shutdown options.

Purpose: Select the Log out option.

#### 11.2 Shut down the operating system.

Purpose: Select Shut Down and allow Kali Linux to power off cleanly.


## 7. Installation Verification Checklist

| Check | Expected Result | Status |
| --- | --- | --- |
| Host CPU | Minimum 4 cores and 8 logical processors verified |   |
| Virtualization | Virtualization technology enabled |   |
| Memory | Minimum 8 GB RAM available; 16 GB+ recommended |   |
| Storage | At least 120 GB free on internal storage |   |
| VMware | VMware Workstation Pro opens successfully |   |
| Kali VM | Kali Linux VM is visible in VMware |   |
| Network | `ip a` shows an assigned IP address |   |
| Internet | `ping -c 4 google.com` receives responses |   |
| Snapshot | Working-state snapshot created successfully |   |
| Shutdown | Kali Linux shuts down cleanly |   |

## 8. Notes and Operational Guidance

- Use an internal drive with sufficient free space for virtual-machine files.

- The source procedure creates D:\VM\Kali Linux when the C: drive does not have enough free space.

- The IP address assigned to Kali Linux can vary depending on the virtual networking configuration.

- A snapshot preserves the VM state at a point in time and can be used for recovery after configuration changes.

- Keep a known-good snapshot before performing lab exercises that may change the VM configuration.

## 9. Troubleshooting

| Issue | Possible Check | Resolution / Next Action |
| --- | --- | --- |
| VM does not start | Check whether virtualization is enabled. | Enable virtualization and retry the VM startup. |
| VM is slow | Check RAM, CPU, and SSD availability. | Confirm the host meets the documented requirements and close unnecessary applications. |
| Insufficient storage | Check free space on C: or D:. | Use an internal drive with adequate space, such as the D: drive used in the source procedure. |
| No IP address in Kali | Run `ip a`. | Verify that the VM has a network interface and then retry the connectivity test. |
| Internet test fails | Run `ping -c 4 google.com`. | Check VM network connectivity and retry the test. |
| Need to undo lab changes | Check available snapshots. | Revert to the known-good snapshot. |

## 10. Completion Criteria

The installation is considered complete when VMware Workstation Pro launches successfully, the Kali Linux virtual machine is available in VMware, the VM receives an IP address, Internet connectivity is verified, a working snapshot is created, and the VM can be shut down cleanly.


## 11. Conclusion

Following this guide provides a structured process for preparing a Windows host, installing VMware Workstation Pro, deploying Kali Linux, validating the virtual environment, and establishing a recovery point. The resulting virtual lab can be used as a controlled environment for cybersecurity learning, testing, and

development activities.

