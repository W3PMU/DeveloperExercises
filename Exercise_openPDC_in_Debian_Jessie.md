[![The Open Source Phasor Data Concentrator](openPDC_Logo.png)](openPDC_Home.md "The Open Source Phasor Data Concentrator")

|   |   |   |   |   |
|---|---|---|---|---|
| **[Grid Protection Alliance](http://www.gridprotectionalliance.org "Grid Protection Alliance Home Page")** | **[openPDC Project](https://github.com/GridProtectionAlliance/openPDC "openPDC Project on GitHub")** | **[Documentation](openPDC_Documentation_Home.md "openPDC Documentation Home Page")** | **[Exercises](Developer_Exercises.md)** | **[Latest Release](https://github.com/GridProtectionAlliance/openPDC/releases "openPDC Releases Home Page")** |

***This document is an exercise procedure for setting up and testing concepts.***

---

# openPDC in Debian Jessie

This is a *cookbook recipe* style exercise procedure for setting up an openPDC Server virtual machine. This procedure was developed and tested using specified operating systems, software versions, and installation sequence. However, with appropriate modifications, this procedure should be adaptable to work in other hardware and software platforms.

- [Platform](#platform)
    - [Platform Description](#platform-description)
    - [Platform Configuration](#platform-configuration)
        - [`GPA-VBOX` Platform Host Server](#gpa-vbox-platform-host-server)
        - [`OPDC-D86` openPDC Server virtual machine](#opdc-d86-openpdc-server-virtual-machine)
    - [Host Server Setup](#host-server-setup)
        - [DNS Configuration](#dns-configuration)
        - [VirtualBox Virtual Machines Setup](#virtualbox-virtual-machines-setup)
            - [IMPORTANT: PASSWORDS](#important-passwords)
    - [`OPDC-D86` Server, Initial Setup](#opdc-d86-server-initial-setup)
- [`OPDC-D86` Server, GPA Software Installation](#opdc-d86-server-gpa-software-installation)

---

## Platform

### Platform Description

This example uses a Windows 10 Host PC, named [`GPA-VBOX`](#gpa-vbox-platform-host-server) running VirtualBox to host virtual machines configured with various operating systems and GPA software.   

The virtual machines will be created with a clean operating system and software installed for this example.  This document will try to highlight the non-default customized installation and configuration steps.  This document does not include many *default* installation and configuration steps.

### Platform Configuration

#### **`GPA-VBOX`** Platform Host PC
    - Windows 10 Enterprise 2016 LTSB with Oracle VirtualBox 5.1.12 for hosting virtual machines
    - CPU = Intel i7, 2.8GHz, Laptop
    - RAM = 16GB, 2133 MHz, non-ECC
    - WiFi Ethernet with Internet access

#### **`OPDC-D86`** openPDC Server virtual machine
    - OS = Debian Jessie 8.6.0 amd64 from netinst.iso 
    - Software = **GPA Software**
    - CPU = 2 virtual cores
    - RAM = 2048MB standard (not dynamic)
    - VHD = 64GB virtual hard drive

---

### Host Server Setup

In this example, the *Host Server* is a general purpose physical server whose function is providing a Hyper-V infrastructure to run the virtual machines and local DNS service.  Setting up the *Host Server* is beyond the scope of this example.  However, the only significant *Host Server* setup beyond a clean Windows install is the installation of Hyper-V and DNS services.

#### DNS Configuration

The Host Server *DNS service* is optional.  The *DNS service* provides reliable and easy to manage Host Name to IP address resolution. This example will use *static IPv4 addresses* for all of the machines.

This example's local area network (LAN) IP Address range is `192.168.1.0 to 192.168.1.255`. Your network will not likely use the same IP Addresses. Also the `gpa.net` domain name is arbitrary. If using a different domain name, make sure it does not conflict with a *real Internet domain* you may want to access. Also, make sure to configure the DNS server's to *Forwarders* properties to resolve Internet side domains' host names.

1. Create a **Forward Lookup Zone** for the domain named:  `gpa.net`
2. Under the `gpa.net` zone, create the following **Host A** records:
    - `GPA-HOST     A  192.168.1.249`
    - `OPDC-01      A  192.168.1.110`
    - `PMU-TESTER   A  192.168.1.120`
3. Set the DNS Server's **Forwarders** properties to include your favorite ISP's DNS service or public DNS service.  This example uses Google's public DNS.
    - `8.8.8.8    google-public-dns-a.google.com`

#### Hyper-V Virtual Machines Setup

This example uses [Microsoft Developer Network (**MSDN**)](https://msdn.microsoft.com) subscription releases of the Windows operating system software in ISO file format. The ISO filenames in this document are renamed to be simplified.

##### **IMPORTANT: PASSWORDS**

In Production Deployments, complex passwords are desireable.  However, in these cookbook scenarios, certain test procedures may be easier to troubleshoot if your passwords are at least 8 alpha-numeric characters long, with mixed character cases, and at least 1 numeric digit.  For now, avoid short simple passwords and avoid using symbols in the passwords.

---

### `OPDC-01` Server, Initial Setup

- 1. Download the `windows_server_2016.iso` file to the [`GPA-HOST`](#gpa-host--platform-host-server) server
- 2. On the [`GPA-HOST`](#gpa-host--platform-host-server) server: create the [`OPDC-01`](#opdc-01--openpdc-server-virtual-machine) openPDC Server virtual machine.
    - Configure [`OPDC-01's`](#opdc-01--openpdc-server-virtual-machine) Hyper-V *Settings* as described in the earlier [Platform Configuration](#platform-configuration) section and assign the `windows_server_2016.iso` image file to its DVD drive.
- 3. Start the `OPDC-01` virtual machine and run the Windows installation.  In the *Windows Setup* dialog's "Select the operating system..." screen, select "Windows Server 2016 Standard (Desktop Experience)"
- 4. During setup, you will be prompted to enter an appropriate password for the *Administrator* account. The *Administrator* account will only be used for software installation and configuration changes requiring elevated privileges.
- 5. Configure the static IP address
    - Open the *`Control Panel\Network and Internet\Network and Sharing Center`*
    - Open the *Ethernet / Properties* and open its *Internet Protocol Version 4 (TCP/IPv4) / Properties* and set the following values:
        - `IP address:            192.168.1.110` - set to match your DNS for `OPDC-01.gpa.net`
        - `Subnet mask:           255.255.255.0` - set to your network's subnet mask
        - `Default gateway:       192.168.1.1  ` - set to your Router's LAN IP address
        - `Preferred DNS server:  192.168.1.249` - set to the `GPA-HOST` server's IP address
    - *Ping* stuff to test the network and DNS configuration.

```
C:\Users\Administrator> ping gpa-host.gpa.net
    Pinging gpa-host.gpa.net [192.168.1.249] with 32 bytes of data:
    Reply from 192.168.1.249: bytes=32 time<1ms TTL=128
    ...
C:\Users\Administrator> ping google-public-dns-a.google.com
    Pinging www.google.com [8.8.8.8] with 32 bytes of data:
    Reply from 8.8.8.8: bytes=32 time=20ms TTL=45
    ...
C:\Users\Administrator> ping time.nist.gov
    Pinging ntp1.glb.nist.gov [132.163.4.102] with 32 bytes of data:
    Request timed out.
```

- 6. In *`Control Panel\Clock, Language, and Region`* click the "Set the time and date"
    - In the *Date and Time* tab, set the date and time and set the local time zone
    - Set the local time zone
    - In the *Internet Time* tab, click the *Change settings...* button and set the *Server* to `time.nist.gov` then click *Update now* and look for a message like "The clock was successfully synchronized with time.nist.gov on..."
- 7. If everything is working so far, run Windows Update and take a coffee break!
- 8. Reboot after Windows Updates are downloaded and let them install by rebooting.
- 9. In *`Control Panel\System and Security\System`* click the *Change Settings* link in the *Computer name, domain, and workgroup settings section.
    - In the *System Properties / Computer Name* tab, click the *Change...* button.
    - In the *Computer Name/Domain Changes* dialog, 
        - change the *Computer name* value to `OPDC-01`
        - change the *Workgroup* value to `GPA.NET`
        - click the *More...* button and set the *Primary DNS suffix of this computer" value to `gpa.net`
        - close the dialogs and reboot 
- 10. Optional: In *`Control Panel\System and Security\System`* 
    - Enable Remote Desktop: click the *Remote Settings* link and select "Allow remote connetions to this computer."
    - Adjust for Best Performance: click the *Advanced system settings* link
        - In the *System Properties / Advanced* tab's *Performance* section, click the *Settings...* button
        - Click the *Adjust for best performance* radio option, and select only the minimum Custom features desired
- 11. After rebooted, *Shut Down* the virtual machine and create a Hyper-V Checkpoint recording of this basic installation configuration
- 12. In *Computer Management / Local Users and Groups / Users*, create a User Account and [**Password**](#important-passwords)
    - The user name in this example is:  `cosine`
    - If you enabled Remote Desktop, add the `cosine` user to the `Remote Desktop Users` Group

---

---

Dec 29, 2016 - Created by [aj](https://github.com/ajstadlin)

---

Copyright 2017 [Grid Protection Alliance](http://www.gridprotectionalliance.org)