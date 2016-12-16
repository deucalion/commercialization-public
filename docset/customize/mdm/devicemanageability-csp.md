---
title: DeviceManageability CSP
description: The DeviceManageability configuration service provider (CSP) is used retrieve the general information about MDM configuration capabilities on the device. This CSP was added in Windows 10, version 1607.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: FE563221-D5B5-4EFD-9B60-44FE4066B0D2
---

# DeviceManageability CSP


The DeviceManageability configuration service provider (CSP) is used retrieve the general information about MDM configuration capabilities on the device. This CSP was added in Windows 10, version 1607.

The following diagram shows the DeviceManageability configuration service provider in a tree format.

![devicemanageability csp diagram](images/provisioning-csp-devicemanageability.png)

<a href="" id="--device-vendor-msft-devicemanageability"></a>**./Device/Vendor/MSFT/DeviceManageability**  
Root node to group information about runtime MDM configuration capability on the target device.

<a href="" id="capabilities"></a>**Capabilities**  
Interior node.

<a href="" id="capabilities-cspversions"></a>**Capabilities/CSPVersions**  
Returns the versions of all configuration service providers supported on the device for the MDM service.

## Examples


Query for the list of CSPs and each supported CSP version.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Get>
      <CmdID>12345</CmdID>
      <Item>
        <Target>
          <LocURI>./Device/Vendor/MSFT/DeviceManageability/Capabilities/CSPVersions</LocURI>
        </Target>
      </Item>
    </Get>
    <Final/>
  </SyncBody>
</SyncML>
```

Result of the query.

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
   <SyncHdr/>
   <SyncBody>
   <Status>
      <CmdID>1</CmdID>
      <MsgRef>1</MsgRef>
      <CmdRef>0</CmdRef>
      <Cmd>SyncHdr</Cmd>
      <Data>200</Data>
   </Status>
   <Status>
      <CmdID>2</CmdID>
      <MsgRef>1</MsgRef>
      <CmdRef>2</CmdRef>
      <Cmd>Get</Cmd>
      <Data>200</Data>
   </Status>
   <Results>
      <CmdID>3</CmdID>
      <MsgRef>1</MsgRef>
      <CmdRef>2</CmdRef>
      <Item>
         <Source><LocURI>./Device/Vendor/MSFT/DeviceManageability/Capabilities/CSPVersions</LocURI></Source>
         <Meta><Format xmlns="syncml:metinf">xml</Format></Meta>
         <Data>&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;DeviceManageability Version="com.microsoft/1.0/MDM/DeviceManageability"&gt;
  &lt;Capabilities&gt;
    &lt;CSPVersions&gt;
      &lt;CSP Node="./DevDetail" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./DevInfo" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/AssignedAccess" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/ClientCertificateInstall" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/DeviceManageability" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/EnterpriseDataProtection" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/EnterpriseDesktopAppManagement" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/EnterpriseModernAppManagement" Version="1.1"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/PassportForWork" Version="1.1"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/Policy" Version="4.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/Reboot" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/RootCATrustedCertificates" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/VPNv2" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/WindowsAdvancedThreatProtection" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Device/Vendor/MSFT/WindowsLicensing" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./SyncML/DMAcc" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/ActiveSync" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/ClientCertificateInstall" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/EMAIL2" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/EnterpriseDesktopAppManagement" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/EnterpriseModernAppManagement" Version="1.1"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/PassportForWork" Version="1.1"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/Policy" Version="4.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/RootCATrustedCertificates" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/SecureAssessment" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/VPNv2" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./User/Vendor/MSFT/WiFi" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/ActiveSync" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/AppLocker" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/CertificateStore" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/DMClient" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/Defender" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/DeviceLock" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/DeviceStatus" Version="1.1"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/DiagnosticLog" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/EMAIL2" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/EnterpriseModernAppManagement" Version="1.1"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/HealthAttestation" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/Maps" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/NodeCache" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/PassportForWork" Version="1.1"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/Policy" Version="4.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/RemoteFind" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/RemoteWipe" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/Reporting" Version="2.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/SharedPC" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/Update" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/VPNv2" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./Vendor/MSFT/WiFi" Version="1.0"&gt;&lt;/CSP&gt;
      &lt;CSP Node="./cimv2" Version="1.0"&gt;&lt;/CSP&gt;
    &lt;/CSPVersions&gt;
  &lt;/Capabilities&gt;
&lt;/DeviceManageability&gt;
         </Data>
      </Item>
   </Results>
   <Final/>
   </SyncBody>
</SyncML>
```

 

 





