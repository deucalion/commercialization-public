---
author: joshbax-msft
title: DatabaseProjectManager Members
description: DatabaseProjectManager Members
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b7c47a78-d85a-4905-a669-035167278594
---

# DatabaseProjectManager Members


The following table lists the members exposed by the **TestResult** type.

## Protected Constructors


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>DatabaseProjectManager</strong></p></td>
<td><p>Overloaded.</p></td>
</tr>
</tbody>
</table>

 

## Public Properties


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ConnectionType</p></td>
<td><p>Overridden. This property represents the underlying database connection type.</p></td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td><p>This property represents the major version of the Windows HCK Controller. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
</tr>
<tr class="odd">
<td><p>VersionString</p></td>
<td><p>This property represents the version of the Windows HCK Controller and its content. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
</tr>
</tbody>
</table>

 

## Public Methods


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CreateDeviceFamily</p></td>
<td><p>Overridden. This method creates a new device family with the given name.</p></td>
</tr>
<tr class="even">
<td><p>CreateProject</p></td>
<td><p>Overridden. This method creates a new Project and adds it to the project collection.</p></td>
</tr>
<tr class="odd">
<td><p>DeleteDeviceFamily</p></td>
<td><p>Overridden. This method deletes a named Device Family.</p></td>
</tr>
<tr class="even">
<td><p>DeleteProject</p></td>
<td><p>Overridden. This method deletes a named project.</p></td>
</tr>
<tr class="odd">
<td><p>Dispose</p></td>
<td><p>This method implements the IDisposable interface. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
</tr>
<tr class="even">
<td><p><strong>Equals</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetDeviceFamilies</strong></p></td>
<td><p>Overridden. This method retrieves a list of available DeviceFamilies.</p></td>
</tr>
<tr class="even">
<td><p>GetFeatures</p></td>
<td><p>Overridden. This method features all of the features stored in the Windows HCK.</p></td>
</tr>
<tr class="odd">
<td><p>GetFilters</p></td>
<td><p>Overridden. This method returns all the filters installed in the system.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetHashCode</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
<tr class="odd">
<td><p>GetPlatforms</p></td>
<td><p>Overridden.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetProductTypes</strong></p></td>
<td><p>Overridden.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetProject</strong></p></td>
<td><p>Overridden. This method loads an existing project into the collection.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetProjectInfoList</strong></p></td>
<td><p>Overridden. This method retrieves a list of project information.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetProjectNames</strong></p></td>
<td><p>Overridden. This method retrieves a list of project names.</p></td>
</tr>
<tr class="even">
<td><p><strong>GetProjectSummary</strong></p></td>
<td><p>Overridden.</p></td>
</tr>
<tr class="odd">
<td><p>GetRequirements</p></td>
<td><p>Overridden. This method retrieves the list of requirements in the Windows HCK.</p></td>
</tr>
<tr class="even">
<td><p>GetRootMachinePool</p></td>
<td><p>Overridden. This method retrieves the root machine pool.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetType</strong></p></td>
<td><p>(Inherited from Object)</p></td>
</tr>
<tr class="even">
<td><p><strong>ToString</strong></p></td>
<td><p>(Inherited from Object)</p></td>
</tr>
</tbody>
</table>

 

## Protected Methods


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dispose</p></td>
<td><p>Overridden. This method implements the <strong>IDisposable</strong> interface.</p></td>
</tr>
<tr class="even">
<td><p><strong>Finalize</strong></p></td>
<td><p>This method finalizes an instance of the <strong>ProjectManager</strong> class. (Inherited from [ProjectManager Class](projectmanager-class.md))</p></td>
</tr>
<tr class="odd">
<td><p><strong>MemberwiseClone</strong></p></td>
<td><p>(Inherited from <strong>Object</strong>)</p></td>
</tr>
</tbody>
</table>

 

 

 





