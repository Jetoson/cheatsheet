# Virtual Machine Management
```Powershell
# List all virtual machines
Get-VM
```

```Powershell
# Start a virtual machine
Start-VM -Name "YourVMName"
```

```Powershell
# Stop a virtual machine (force)
Stop-VM -Name "YourVMName" -Force
```

```Powershell
# Create a new virtual machine
New-VM -Name "NewVM" -MemoryStartupBytes 2GB -NewVHDPath "C:\Path\to\YourVM.vhdx" -NewVHDSizeBytes 50GB
```

```Powershell
# Rename a virtual machine
Rename-VM -VMName "OldVMName" -NewName "NewVMName"
```

```Powershell
# Get detailed information about a virtual machine
Get-VM "YourVMName" | Format-List *
```

```Powershell
# List running virtual machines only
Get-VM | Where-Object { $_.State -eq 'Running' }
```

# Memory and CPU Configuration
```Powershell
# Configure dynamic memory for a virtual machine
Set-VMMemory -VMName "YourVMName" -DynamicMemoryEnabled $true -MinimumBytes 512MB -MaximumBytes 4GB
```

```Powershell
# Change startup memory
Set-VMMemory -VMName "YourVMName" -StartupBytes 2GB
```

```Powershell
# Adjust memory buffer
Set-VMMemory -VMName "YourVMName" -Buffer 20%
```

```Powershell
# Set number of virtual processors
Set-VMProcessor -VMName "YourVMName" -Count 4
```

```Powershell
# Set CPU relative weight
Set-VMProcessor -VMName "YourVMName" -RelativeWeight 200
```

```Powershell
# Enable nested virtualization
Set-VMProcessor -VMName "YourVMName" -ExposeVirtualizationExtensions $true
```

# Storage (VHD / DVD)
```Powershell
# List all virtual hard disks
Get-VHD
```

```Powershell
# Create a new dynamic VHD
New-VHD -Path "C:\Path\to\YourNewVHD.vhdx" -SizeBytes 100GB -Dynamic
```

```Powershell
# Attach a VHD to a virtual machine
Add-VMHardDiskDrive -VMName "YourVMName" -Path "C:\Path\to\YourExistingVHD.vhdx"
```

```Powershell
# Remove a VHD from a virtual machine
Remove-VMHardDiskDrive -VMName "YourVMName" -ControllerType SCSI -ControllerNumber 0 -ControllerLocation 1
```

```Powershell
# Attach an ISO (DVD drive)
Add-VMDvdDrive -VMName "YourVMName" -Path "C:\Path\to\YourISO.iso"
```
# Checkpoints (Snapshots)
```Powershell
# Create a checkpoint
Checkpoint-VM -VMName "YourVMName" -SnapshotName "YourSnapshotName"
```

```Powershell
# List checkpoints for a VM
Get-VMSnapshot -VMName "YourVMName"
```

```Powershell
# Restore a specific checkpoint
Restore-VMSnapshot -VMName "YourVMName" -Name "YourSnapshotName"
```

```Powershell
# Remove a checkpoint
Remove-VMSnapshot -VMName "YourVMName" -Name "YourSnapshotName"
```

```Powershell
# List checkpoints with details
Get-VMSnapshot -VMName "YourVMName" | Select-Object VMName, Name, CreationTime
```

# Export / Import / Cloning
```Powershell
# Export a virtual machine
Export-VM -Name "YourVMName" -Path "C:\Path\to\ExportFolder"
```

```Powershell
# Export only VM configuration
Export-VM -Name "YourVMName" -ConfigurationOnly -Path "C:\Path\to\ConfigurationExport"
```

```Powershell
# Export all virtual machines
Get-VM | Export-VM -Path "C:\Path\to\ExportAllVMs" -NamePrefix "Exported"
```

```Powershell
# Import a virtual machine
Import-VM -Path "C:\Path\to\ExportFolder" -Copy -GenerateNewId
```

```Powershell
# Clone a virtual machine from a snapshot
New-VM -Name "ClonedVM" -VMPath "C:\Path\to\ClonedVM" -Generation 2 -Copy -ReferenceSnapshotName "YourSnapshotName"
```

# Networking
```Powershell
# List virtual switches
Get-VMSwitch
```

```Powershell
# Create a new external virtual switch
New-VMSwitch -Name "YourSwitchName" -SwitchType External -NetAdapterName "YourPhysicalNIC"
```

```Powershell
# Remove a virtual switch
Remove-VMSwitch -Name "YourSwitchName"
```

```Powershell
# Get VM network adapter information
Get-VMNetworkAdapter -VMName "YourVMName"
```

```Powershell
# Assign a static MAC address
Get-VMNetworkAdapter -VMName "YourVMName" | Set-VMNetworkAdapter -StaticMacAddress "00:15:5D:00:01:23"
```

```Powershell
# Configure VLAN ID
Get-VMNetworkAdapter -VMName "YourVMName" | Set-VMNetworkAdapterVlan -Access -VlanId 100
```

# Boot & Integration Services
```Powershell
# Change VM boot order
Set-VMFirmware -VMName "YourVMName" -FirstBootDevice "CD"
```

```Powershell
# Enable Secure Boot
Set-VMFirmware -VMName "YourVMName" -SecureBootTemplate MicrosoftUEFICertificateAuthority
```

```Powershell
# Enable an integration service
Get-VMIntegrationService -VMName "YourVMName" | Enable-VMIntegrationService -Name "GuestServiceInterface"
```

```Powershell
# Disable an integration service
Get-VMIntegrationService -VMName "YourVMName" | Disable-VMIntegrationService -Name "GuestServiceInterface"
```

```Powershell
# Check integration services status
Get-VMIntegrationService -VMName "YourVMName"
```

# Automatic Start / Stop
```Powershell
# Configure VM automatic start
Set-VM -VMName "YourVMName" -AutomaticStartAction Start -AutomaticStartDelay 120
```

```Powershell
# Configure automatic start and stop behavior
Set-VM -VMName "YourVMName" -AutomaticStartAction Start -AutomaticStartDelay 120 -AutomaticStopAction ShutDown -AutomaticStopDelay 60
```

```Powershell
Replication
# Enable VM replication
Enable-VMReplication -VMName "YourVMName" -ReplicaServerName "TargetHyperVHost" -ReplicaServerPortNumber 80 -AuthenticationType Kerberos
```

```Powershell
# Start replication
Start-VMReplication -VMName "YourVMName" -ReplicaServerName "TargetHyperVHost" -ReplicaServerPortNumber 80 -AuthenticationType Kerberos
```

```Powershell
# Stop replication
Stop-VMReplication -VMName "YourVMName" -ReplicaServerName "TargetHyperVHost"
```

```Powershell
# Check replication status
Get-VMReplication -VMName "YourVMName"
```

```Powershell
# Check replication health
Get-VMReplication -VMName "YourVMName" | Measure-VMReplication
```

```Powershell
# Set replication frequency
Set-VMReplication -VMName "YourVMName" -ReplicationFrequencyInSec 300
```

```Powershell
# Enable replication compression
Set-VMReplication -VMName "YourVMName" -ReplicationEnableCompression $true
```

```Powershell
# Enable replication for multiple VMs
Get-VM -Name "VM1","VM2" | Enable-VMReplication -ReplicaServerName "TargetHyperVHost" -ReplicaServerPortNumber 80 -AuthenticationType Kerberos
```

# Host Configuration & Diagnostics
```Powershell
# Display Hyper-V host information
Get-VMHost
```

```Powershell
# Enable Enhanced Session Mode at host level
Set-VMHost -EnableEnhancedSessionMode $true
```

```Powershell
# View Hyper-V VMMS events
Get-WinEvent -LogName Microsoft-Windows-Hyper-V-VMMS-Admin
```

```Powershell
# Configure live migration
Enable-VMMigration -MaxReceiveInterval 500 -AuthenticationType CredSSP
```

```Powershell
# Set host power plan to High Performance
powercfg /s SCHEME_MIN
```

```Powershell
# Disable standby timeouts
powercfg /change standby-timeout-ac 0
powercfg /change standby-timeout-dc 0
```

```Powershell
# Enable VM resource metering
Enable-VMResourceMetering -VMName "YourVMName"
```

```Powershell
# Configure Smart Paging file location
Set-VM -VMName "YourVMName" -SmartPagingFilePath "C:\Path\to\SmartPagingFile"
```
