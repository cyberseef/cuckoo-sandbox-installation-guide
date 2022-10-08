# cuckoo-sandbox-installation-guide

# SPECIFICATIONS

RAM: 6 GB

CPU: 4 Cores

Storage: 80 GB

Host Machine: Ubuntu 20.04 LTS or above

Link: https://ubuntu.com/download/desktop

Guest Machine: Windows 7 Ultimate

Link: Included in Setup Instructions as You Follow

# VMWare Settings

1. Open Settings of the Virtual Machine
2. Open Hardware Tab
3. Enable "Virtualize Intel VT-x/EPT or AMD/RVI"

# Oracle VirtualBox Settings

1. Open Settings of the Virtual Machine
2. Go to System in Settings
3. Open Acceleration Tab
4. Enable "Enable Nested Paging" in Hardware Virtualization
5. Go to Processor Tab
6. Enable "Enable Nested VT-x/AMD-V" in Extended Features

NOTE: After Setting Your Desired Hypervisor as Stated Above, Open [Setting-Up Host Machine](https://github.com/cyberseef/cuckoo-sandbox-installation-guide/blob/91191b86fd0902e7862e36e83f2c7e896daf0ebf/Setting-Up%20Host%20Machine.MD)
