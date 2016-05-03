---
author: joshbax-msft
title: Scanner Testing Prerequisites
description: Scanner Testing Prerequisites
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: ed9185d0-42b3-4929-9784-05ae74a101b2
---

# Scanner Testing Prerequisites


This section describes the tasks that you must complete before you test a scanner by using the Windows Hardware Certification Kit (Windows HCK):

-   [Review the hardware requirements](#bkmk-hck-scanner-hr).

-   [Review the software requirements](#bkmk-hck-scanner-sr).

-   [Configure the test computers](#bkmk-hck-scanner-tc).

## <a href="" id="bkmk-hck-scanner-hr"></a>Hardware requirements


The following hardware is required for scanner testing. Additional hardware may be required if the test device provides bus-specific support. See the test description for each bus-specific test to determine whether there are additional hardware requirements.

-   Basic Windows HCK test setup (Controller and Studio). See [Windows HCK Getting Started](windows-hck-getting-started.md)

-   One test computer.

    **Note**  
    All computers must meet the Windows HCK requirements. If two test computers are required, both computers must be in the same computer pool. For more information, see [Windows HCK Prerequisites](windows-hck-prerequisites.md).

    For testing networking capabilities, the test computer that the scanner is physically attached to is referred to as the System Under Test (SUT) and the other computer is referred to as the support computer.

     

-   The test scanner

-   One standalone wireless network adapter that supports SoftAP (for example, a D-Link WDA-1320 Desktop Adapter), and a Wireless router if the test scanner includes wireless networking capabilities.

-   One stand-alone network adapter (if the test computer does not include an integrated network adapter) and an Ethernet hub or switch if the test scanner includes network scanning capabilities.

-   One USB cable and one USB 3.0 hub for testing scanners that support USB 3.0; or a USB 2.0 hub for testing a scanner that supports USB 2.0

**Note**  
Testing a device to obtain Server Device certification requires that the system being used to test the device supports four processors and a minimum of 1 GB of RAM. These system capabilities are required for testing the device and driver for their Rebalance, D3 State and Multiple Processor Group functionality. You do not need a computer that actually has more than 64 processors to test your device.

If a pool of test computers is used to test devices, at least one computer in the pool must contain four processors and a minimum of 1 GB of RAM. Additionally, that computer must contain the device and driver being tested. As long as the driver is the same on all computers in the pool, the schedule will be created to run against all computers.

For those tests that do not include a driver to test, such as testing a hard drive, the Windows HCK scheduler will constrain the tests that validate the device’s and driver’s Rebalance, D3 State and Multiple Processor Groups functionality to run on the default computer. This computer should also be manually configured to have multiple processor groups. The default computer is the first one listed. Test personnel, in this case, should ensure that this first computer meets these minimum hardware requirements.

 

**Note**  
Except for para-virtualization drivers (as defined by Logo Program Requirement Policy-0020), physical devices and their associated drivers being tested for a server logo or signature may not be tested in virtual machines using any form of virtualization. This is because not all virtualization products support the underlying functionality needed to pass the tests relating to Multiple Processor Groups, Device Power Management, Device PCI functionality, and so on.

 

## <a href="" id="bkmk-hck-scanner-sr"></a>Software requirements


It is good practice to clean-install the operating system on client systems before final test passes to ensure that the system is in a known clean state.

The following software is required to run the scanner tests:

-   The AppVerifier application.

    **Note**  
    AppVerifier is installed during the Windows HCK client application installation.

     

-   The driver package being tested installed on a client system

-   Desktop Experience, for computers with Windows Server 2008 R2 installed. Desktop Experience ensures that the scanner tests run correctly. Run the following command from the command prompt to install Desktop experience: **ocsetup.exe DesktopExperience /quiet /norestart**

## <a href="" id="bkmk-hck-scanner-tc"></a>Test system configuration


To configure the test computer for scanner testing, follow these steps:

1.  Install the appropriate Windows operating system on the test computer.

2.  Configure the test computer for your test network (the network that contains the Windows HCK Studio and Windows HCK Controller.

3.  Connect the SUT and the support computer to an Ethernet switch or hub to test wired networking capabilities of your scanner. Connect a wireless router to the support computer to test wireless capabilities.

4.  Install the manufacturer-supplied device driver on the test computer, if the device requires one that is not included with Windows.

5.  Attach the test scanner to the test computer using a USB cable.

6.  Check that the scanner functions properly on the test computer.

7.  Install the Windows HCK client application on the test computer.

8.  Create a computer pool and move the test computers to that pool by using Windows HCK Studio.

Make sure that the test computer is in the ready state before you begin your testing. If a test requires parameters to be set before it is run, a dialog box will be displayed for that test. Review the specific test topic for more information.

Some Windows HCK tests require user intervention. When running tests for a submission, it is a best practice to run the automated tests in a block separately from manual tests. This prevents a manual test from interrupting completion of an automated test.

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20Scanner%20Testing%20Prerequisites%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



