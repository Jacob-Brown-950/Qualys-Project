# Qualys-Lab

## Objective

Welcome to my Vulnerability Management Lab! In this project, I set up a lab using Qualys Community Edition to practice identifying and remediating vulnerabilities in a Windows 10 environment. This hands-on experience is perfect for anyone looking to dive into the world of vulnerability management—especially for those of us starting our careers in IT!

### Skills Learned

Through this project, I picked up some valuable skills, including:

- **Installed and Deployed Qualys Virtual Scanner Appliance**: Successfully imported the scanner into VirtualBox and accessed it via the Qualys Cloud Platform.
- **Executed the Vulnerability Management Lifecycle**: Gained experience in the stages of Discovery, Prioritization, Assessment, Reporting, Remediation, and Verification within a virtualized environment.
- **Leveraged Qualys for Vulnerability Management**: Managed vulnerability scanning and effectively addressed identified vulnerabilities.
- **Identified Deprecated Software**: Detected outdated software on a Windows 10 machine, remediated the vulnerabilities, and verified that the software was no longer vulnerable.
- **Understanding the Importance of Updates**: Recognized the significance of keeping applications and operating systems up to date to minimize security risks.

### Tools Used

Here’s a quick look at the tools I used for this lab:

- **Qualys Community Edition**: Common tool for vulnerability scanning.
- **Oracle VirtualBox**: Perfect for simulating a Windows 10 environment.
- **Outdated Software**: I intentionally used older versions of VLC Media Player (version 1.1.1) and Firefox (version 1.4.0) to create some vulnerability flags.

## Table of Contents

1. [Introduction](#introduction)
2. [Setting Up the Windows 10 VM](#setting-up-the-windows-10-vm)
3. [Creating Vulnerabilities](#creating-vulnerabilities)
4. [Qualys Virtual Scanner Setup](#qualys-virtual-scanner-setup)
5. [Running the Scans](#running-the-scans)
6. [Remediation](#remediation)
7. [Conclusion](#conclusion)

## Introduction

In this guide, I’ll walk you through the steps I took to set up my vulnerability management lab. It’s all about simulating a Windows 10 environment where I could play around with intentionally outdated software.

## Setting Up the Windows 10 VM

First things first, we need a Windows 10 virtual machine (VM). Here’s how I got that rolling:

1. **Download Oracle VirtualBox**:
   - Head over to the [Oracle VirtualBox website](https://www.virtualbox.org/) and grab the latest version that fits your OS. Installation is pretty straightforward—just follow the prompts!

2. **Get a Windows 10 ISO File**:
   - You can download the Windows 10 ISO from the [Microsoft website](https://www.microsoft.com/en-us/software-download/windows10). Just pick the edition and language you want, and you’re good to go.

3. **Create a Windows 10 VM**:
   - Open up VirtualBox and click "New" to create your VM. Set it up with a name, type, and version (Windows 10). Allocate at least 4 GB of memory for a smooth experience and create a virtual hard disk (20 GB is usually sufficient).

4. **Set a Static IP Address**:
   - In the VM's network settings, opt for "Bridged Adapter." This lets your VM communicate on the same network as your host machine. I recommend setting a static IP to avoid any DHCP issues later.

## Creating Vulnerabilities

Now for the fun part—creating some vulnerabilities! Here’s how I did it:

1. **Download VLC Media Player (version 1.1.1)**:
   - I went to the [VLC Releases](https://download.videolan.org/pub/videolan/vlc/1.1.1/) page, grabbed the installer for Windows, and set it up in my VM.

2. **Install Firefox (version 1.4.0)**:
   - Next, I visited the [Mozilla Firefox Releases](https://ftp.mozilla.org/pub/firefox/releases/1.0.4/) directory to get the Windows installer for version 1.4.0. After downloading, I installed it in the VM as well.

## Qualys Virtual Scanner Setup

With my VM ready and the vulnerabilities in place, it was time to set up Qualys:

1. **Sign Up for Qualys Community Edition**:
   - Go to the [Qualys Community Edition page](https://www.qualys.com/community-edition/) and create your account. It’s free and gives you access to some awesome tools!

2. **Set Up the Qualys Virtual Scanner**:
   - After signing up, download the virtual scanner. Then, in VirtualBox, select "Import Appliance" and choose the scanner file to import it into your setup.

3. **Configure an IP Range in Qualys**:
   - Log into your Qualys account, navigate to the "Scans" section, and create a new scan by specifying the IP range that includes your Windows 10 VM.

4. **Disable Windows Firewall Temporarily**:
   - To make sure the scans go smoothly, I disabled the Windows Firewall on the VM. You can do this by going to Control Panel > System and Security > Windows Defender Firewall > Turn Windows Defender Firewall on or off.

## Running the Scans

Once everything was set up, I ran a couple of scans to see what vulnerabilities popped up:

1. **Unauthenticated Scan**: This gave me a glimpse of open ports but not much detail on vulnerabilities.
   - **Vulnerabilities Found**: 2
   - [View PDF](https://github.com/Jacob-Brown-950/Qualys-Lab/raw/main/Regular%20Scan%20(Not%20Authenticated).pdf)

2. **Authenticated Scan**: This scan really highlighted the outdated applications I had installed.
   - **Vulnerabilities Found**: 120
   - [View PDF](https://github.com/Jacob-Brown-950/Qualys-Lab/raw/main/Authenticated%20Scan.pdf)

## Remediation

After identifying the vulnerabilities, I uninstalled the outdated software and performed another authenticated scan to check my progress:
   - **Vulnerabilities Found After Software Removal**: 52
   - [View PDF](https://github.com/Jacob-Brown-950/Qualys-Lab/raw/main/Authenticated%20Scan%20After%20Removing%20Outdated%20Software.pdf)

### Patching and Configuration Changes

I also noticed vulnerabilities related to missing Windows security updates and certain settings. After applying those patches and making some registry and configuration changes, I ran one last scan:
   - Changes Made:
     - Set Allow deployment of unsigned packages to Disabled.
     - Changed default local account names.
     - Disabled SMBv1 and ensured SMB Signing.
     - Adjusted Autoplay Settings.
   - **Final Vulnerabilities After Updates and Changes**: 11
   - [View PDF](https://github.com/Jacob-Brown-950/Qualys-Lab/raw/main/Authenticated%20Scan%20After%20Updates.pdf)

## Conclusion

Through this project, I successfully identified and fixed several vulnerabilities. It really drove home the importance of keeping both applications and operating systems up to date to minimize security risks. I hope this guide inspires you to set up your own vulnerability management lab and start your journey in IT!
