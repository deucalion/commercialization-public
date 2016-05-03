---
author: joshbax-msft
title: Ifdtest2 Part D (SC Reader LOGO) - (Manual Test)
description: Ifdtest2 Part D (SC Reader LOGO) - (Manual Test)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 58877c8e-0ac9-4afb-bc35-dbe34f0b3476
---

# Ifdtest2 Part D (SC Reader LOGO) - (Manual Test)


This test verifies the functionality of the smart card reader by validating the PC/SC workgroup test cards. Part D requires the PC/SC test cards.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>Device.Input.SmartCardReader.PinDataEntryKeyboardCompliesWithIso Device.Input.SmartCardReader.Supports258And259BytePackets Device.Input.SmartCardReader.SupportsDirectAndInverseConvention Device.Input.SmartCardReader.SupportsNegotiableAndSpecificModes Device.Input.SmartCardReader.SupportsResetCommand Device.Input.SmartCardReader.UsbCcidIssuesNak</p>
<p>[See the device hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254483)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows 7 (x64) Windows 7 (x86) Windows RT (ARM-based) Windows 8 (x64) Windows 8 (x86) Windows Server 2012 (x64) Windows Server 2008 R2 (x64) Windows Server 2008 x64 Windows Server 2008 x86Windows RT 8.1Windows 8.1 x64Windows 8.1 x86Windows Server 2012 R2</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~5 minutes</p></td>
</tr>
<tr class="even">
<td><p><strong>Categories</strong></p></td>
<td><p>Certification Functional</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>Manual</p></td>
</tr>
</tbody>
</table>

 

## Running the test


Before you run the test, complete the test setup as described in the test requirements: [Smart Card Reader Testing Prerequisites](smart-card-reader-testing-prerequisites.md).

## Troubleshooting


For troubleshooting information, see [Troubleshooting Device.Input Testing](troubleshooting-deviceinput-testing.md).

## More information


This test verifies the functionality of the smart card reader by validating the revision two of the PC/SC workgroup test cards.

The test and its hardware must be able to execute specific IFD tests and produce a test report. Specific requirements deal with nominal operation and exceptional operation (error conditions). In addition, these must be applied to all protocols supported by the reader subsystem.

IFDTEST2 performs test cases in three separate test jobs: Reader Interface tests are performed without anything inserted in the reader. Resource Manager Status test cases are performed as a sample card is inserted into and removed from the reader, and do handling of card insertion detection under various conditions (any card can be used for this test).

Card Protocol tests involve operation both with inserted representative ordinarily available smart cards and with special cards that exhibit certain specially programmed behavior. The test cases using ordinarily available cards will perform routine operations on cards selected to represent a variety of communication speed and protocol combinations. These tests have changed with the card-set 2.

**Resource manager status test cases**

Part A

The card monitor test cases check for correct detection of smart card insertion state and correct handling of operations interrupted by the unexpected removal of the card.

1.  Test detection of empty readers using IOCTL\_SMARTCARD\_IS\_PRESENT

2.  Test detection of inserted card using IOCTL\_SMARTCARD\_IS\_PRESENT

3.  Test removal of inserted card using IOCTL\_SMARTCARD\_IS\_ABSENT

4.  Test correct handling of randomly timed card insert and remove actions for 15 seconds

    -   Verify that IOCTL\_SMARTCARD\_IS\_PRESENT and IOCTL\_SMARTCARD\_IS\_ABSENT produce valid results

Part C

The resource manager test cases verify successful completion of state change operations normally expected to be commanded by the smart card resource manager.

1.  Verify IOCTL\_SMARTCARD\_GET\_STATE succeeds without card

2.  Verify returned state is valid

3.  Verify correct return from IOCTL\_SMARTCARD\_IS\_PRESENT

4.  Verify correct return from IOCTL\_SMARTCARD\_IS\_ABSENT

5.  Operator inserts a card

6.  Verify IOCTL\_SMARTCARD\_GET\_STATE succeeds with card inserted

7.  Verify returned state is valid

8.  Verify correct return from IOCTL\_SMARTCARD\_IS\_ABSENT

9.  Cold reset the card

10. Verify card state is SCARD\_NEGOTIABLE

11. Set Card Protocol to T0 or T1

12. Verify success of IOCTL\_SMARTCARD\_POWER to turn off the card

13. Operator removes the card

14. Verify IOCTL\_SMARTCARD\_GET\_STATE succeeds without a card

Part E

The power management test cases verify that the driver returns the correct state information for the reader across hibernation sequences, even when the state of the reader is changed during hibernation by insertion or removal of a card.

1.  Operator removes all cards

2.  Operator hibernates computer

3.  Operator starts computer

4.  Verify reader state SCARD\_ABSENT on return from hibernate

5.  Operator Inserts card

6.  Operator hibernates computer

7.  Operator starts computer

8.  Verify reader state SCARD\_PRESENT on return from hibernate

9.  Operator removes card

10. Operator hibernates computer

11. Operator removes card during hibernate

12. Operator starts computer

13. Verify reader state SCARD\_ABSENT on return from hibernate

14. Operator hibernates computer

15. Operator inserts card during hibernate

16. Operator starts computer

17. Verify reader state SCARD\_PRESENT on return from hibernate

**Reader interface test cases**

Part B

Reader interface test cases check for the correct implementation property and state information at the reader driver.

1.  Check attributes reported by the reader with a sample card inserted

2.  Test that device name reported by the driver is WDM PnP compliant

3.  Test that driver correctly handles attribute read requests with NULL return buffer

4.  Test that driver correctly stops pending i/o requests if the driver is closed and reopened with an i/o operation pending

5.  Test read attributes with no card inserted

    -   SCARD\_ATTR\_VENDOR\_NAME : non-zero-length string

    -   SCARD\_ATTR\_VENDOR\_IFD\_TYPE : non-zero-length string

    -   SCARD\_ATTR\_DEVICE\_UNIT : a 4 byte or larger length value

    -   SCARD\_ATTR\_ATR\_STRING : read attempt fails

    -   SCARD\_ATTR\_DEFAULT\_CLK : 1000 &lt;= value &lt;= 20000

    -   SCARD\_ATTR\_MAX\_CLK : 1000 &lt;= value &lt;= 20000

    -   SCARD\_ATTR\_DEFAULT\_DATA\_RATE : read attempt succeeds

    -   SCARD\_ATTR\_MAX\_DATA\_RATE : read attempt succeeds

    -   SCARD\_ATTR\_MAX\_IFSD : 1 &lt;= value &lt;= 254

    -   SCARD\_ATTR\_CURRENT\_PROTOCOL\_TYPE : read attempt fails

6.  Test read attributes with a card inserted

    -   SCARD\_ATTR\_VENDOR\_NAME : non-zero-length string

    -   SCARD\_ATTR\_VENDOR\_IFD\_TYPE : non-zero-length string

    -   SCARD\_ATTR\_DEVICE\_UNIT : a 4 byte or larger length value

    -   SCARD\_ATTR\_ATR\_STRING : read attempt succeeds

    -   SCARD\_ATTR\_DEFAULT\_CLK : value 1000 &lt;= value &lt;= 20000

    -   SCARD\_ATTR\_MAX\_CLK : value 1000 &lt;= value &lt;= 20000

    -   SCARD\_ATTR\_DEFAULT\_DATA\_RATE : read attempt succeeds

    -   SCARD\_ATTR\_MAX\_DATA\_RATE : read attempt succeeds

    -   SCARD\_ATTR\_MAX\_IFSD : 1 &lt;= value &lt;= 254

    -   SCARD\_ATTR\_CURRENT\_PROTOCOL\_TYPE : value = 0

7.  Read card state with card removed using IOCTL\_SMARTCARD\_GET\_STATE : state &lt;= SCARD\_SWALLOWED

8.  Reset card : verify result is ERROR\_UNRECOGNIZED\_MEDIA

**Card protocol test cases**

Part D

Infineon Technologies PC/SC Compliance Test Card (Card 0 / Unlabeled)

ATR: 3B EF 00 00 81 31 20 49

00 5C 50 43 54 10 27 F8

D2 76 00 00 38 33 00 4D

1.  Attempt read with buffer too small

2.  Waiting time extension request - route request figure to file 0001, read back and verify

3.  Block chaining resync test on file 0002: card accepts first block. Then repeatedly requests retransmission of block 2; host resyncs - expect ERROR\_IO\_DEVICE

4.  Block chaining resync test on file 0002: card repeatedly declares EDC error on block 2; host resyncs - expect ERROR\_IO\_DEVICE

5.  Wrong block sequence by read to file 0003 - expect ERROR\_IO\_DEVICE

6.  Ifsc request file id 0004

7.  Force time-out by read to file 0005 - expect ERROR\_IO\_DEVICE

8.  Read and process result file (A000), parse and report errors

Athena T0 Test Card (Card 1)

ATR: 3B D6 18 00 80 B1 80 6D

1F 03 80 51 00 61 10 30

9E

1.  Reset with long (approx 900 mSec) ATR transmission time

2.  Set Protocol to T0, expect success

3.  Erase all card files by proprietary command, expect success

4.  Create test file 0002, expect success

5.  Select test file 0002, expect success

6.  Write 256 bytes as 4 blocks of 64 bytes, expect success

7.  Read and verify 256 bytes as 4 blocks of 64 bytes, expect success

8.  Write 255 bytes as a single block, expect success. The card will receive the bytes in single-byte mode until 8 bytes remain, at which point the rest of the data will be requested from the host as a single block, expect success

9.  Set receive buffer to 9 bytes and attempt to receive 10 bytes response from card, expect ERROR\_INSUFFICIENT BUFFER

10. Send malformed (Lc inconsistent with data length) select command 00 a4 00 00 08 00, expect ERROR\_INVALID\_PARAMETER

11. Select nonexistent file, expect 6A 82

12. Send command to silence the card (80 00 01 00 01 11), expect ERROR\_SEM\_TIMEOUT

13. Reset the card

14. Send echo command to card to test request wait time extension for extension counts of 1, 2, 5, and 30 extensions, expect success

Athena\\Inverse Convention Test Card (Card 2)

ATR: 3F 96 18 80 01 80 51 00

61 10 30 9F

1.  Reset with long (approx 900 mSec) ATR transmission time

2.  Set Protocol to T0, expect success

3.  Erase all card files by proprietary command, expect success

4.  Create test file 0002, expect success

5.  Select test file 0002, expect success

6.  Write 256 bytes as 4 blocks of 64 bytes, expect success

7.  Read and verify 256 bytes as 4 blocks of 64 bytes, expect success

8.  Write 255 bytes as a single block, expect success. The card will receive the bytes in single-byte mode until 128 bytes remain, at which point the rest of the data will be requested from the host as a single block, expect success

9.  Set receive buffer to 9 bytes and attempt to receive 10 bytes response from card, expect ERROR\_INSUFFICIENT BUFFER

10. Send malformed (Lc inconsistent with data length) select command 00 a4 00 00 08 00, expect ERROR\_INVALID\_PARAMETER

11. Select nonexistent file, expect 6A 82

12. Send command to silence the card (80 00 01 00 01 11), expect ERROR\_SEM\_TIMEOUT

13. Reset the card

14. Send echo command to card to test request wait time extension for extension counts of 1, 2, 5, and 30 extensions, expect success

Axalto 32K eGate Test Card (Card 3)

ATR: 3B 95 18 40 FF 62 01 02

01 04

1.  Attempt set protocol T=1, expect ERROR\_NOT\_SUPPORTED

2.  Set protocol T=0

3.  Authenticate using card transport key, expect success

4.  Clean card state by deleting files from previous runs (Remove RSA public and private key files, the user PIN file, and the test file), expect success

5.  Create new test file 0055, expect success

6.  Test write blocks 1, 25, 75, 128 bytes to test file, expect success

7.  Test read 128 bytes from test file, compare data, expect success

8.  Delete test file 0055, expect success

9.  Create PIN file, expect success

10. Set user PIN to 00000000, expect success

11. Create private key file, expect success

12. Create public key file, expect success

13. Select private key file, expect success

14. Authenticate user who has PIN, expect success

15. Generate key pair, expect success

16. Hash 16 bytes data, expect success

17. Get response data to hash operation, 20 bytes + 2 bytes response, expect success

Infineon SiCrypt Card Module Test Card (Card 4)

ATR: 3B DF 18 00 81 31 FE 67

00 5C 49 43 4D D4 91 47

D2 76 00 00 38 33 00 58

1.  Attempt to set protocol T=0, expect ERROR\_NOT\_SUPPORTED

2.  Set protocol T=1, expect success

3.  Authenticate using PIN 12345678, expect success

4.  Remove files from previous runs if existing

5.  Create new test file 0007, expect success

6.  Select file 0007, expect success

7.  Record system time

8.  Write test blocks of 1, 25, 50, 75, 100, 125, 128 bytes to the card - Read and verify the data after each block write, expect success

9.  Get system time and show elapsed time in seconds for test completion

10. Select file 0007, expect success

11. Write 128 byte block of byte value 55, Read back and verify, expect success

12. Write 128 byte block of byte value AA, Read back and verify, expect success

13. Write 128 byte block of byte value 00, Read back and verify, expect success

14. Write 128 byte block of byte value FF, Read back and verify, expect success

15. Select nonexistent file 7777, expect 9404

16. Select MF by 00 a4 00 00, expect 90 00 (success)

17. Select invalid file 77, expect 94 04

18. Send malformed (Lc inconsistent with data length) select command 00 a4 00 00 08 00, expect 94 04

19. Send malformed (too short) select command by 00 a4 00, expect 67 00

20. Create DF 5555 from the MF, expect success

21. Select into 5555, expect success

22. Create DF 5656 from 5555, expect success

23. Select into 5656, expect success

24. Create File 5757 in DF 5656, expect success

25. Select that file from MF by full path, expect success

26. Write 8 bytes to file, Read back and verify, expect success

27. Delete the selected file, expect success

28. Attempt to select that file by full path, expect 94 04

29. Select and delete DF 5656, expect success

30. Select and delete DF 5555, expect success

31. Select and delete file 0007, expect success

### Running the card reader test

**Warning**  
For the power management test cases in Part D, the computer will hibernate and you may have to remove or reinsert a smart card in the test smart card reader.

 

**Parts A, B, C, and E**

Follow the instructions on the screen for Parts A, B, C, and E by using the cards from the PC/SC workgroup test card-set 2. When you are prompted, insert and then remove each smart card from the test smart card reader.

**Part D**

Follow the instructions on the screen for Part D to complete the four power management test cases. When you are prompted, insert or remove the smart card from the test smart card reader and hibernate or restart the test computer.

To run the Test 1 Card Out/Card Out test case:

1.  Remove the smart card from the test smart card reader.

2.  The computer will automatically hibernate after 15 seconds.

3.  Allow the computer to hibernate for 30 to 60 seconds.

4.  Press the computer power button to bring the computer out of hibernation and continue the test.

5.  When you are prompted, reinsert the smart card in the test smart card reader.

To run the Test 2 Card In/Card Out test case:

1.  Verify that the smart card is in the test smart card reader.

2.  The computer will automatically hibernate after 15 seconds.

3.  Allow the computer to hibernate for 30 to 60 seconds.

4.  Remove the smart card from the test smart card reader.

5.  Press the computer power button to bring the computer out of hibernation.

6.  When you are prompted, reinsert the smart card in the test smart card reader before you start the next test case.

To run the Test 3 Card In/Card In test case:

1.  Verify that the smart card is in the test smart card reader.

2.  The computer will automatically hibernate after 15 seconds.

3.  Allow the computer to hibernate for 30 to 60 seconds.

4.  Press the computer power button to bring the computer out of hibernation.

5.  When you are prompted, remove the smart card from the test smart card reader before you start the next test case.

To run the Test 4 Card Out/Card in test case:

1.  Verify that there is no smart card in the test smart card reader.

2.  The computer will automatically hibernate after 15 seconds.

3.  Allow the computer to hibernate for 30 to 60 seconds.

4.  Reinsert the smart card in the test smart card reader.

5.  Press the computer power button to bring the computer out of hibernation. The smart card reader test is completed.

6.  View the test log files.

7.  Run all of the other required tests.

8.  After you successfully complete all of the tests that are required for this test submission, return the test results.

### Command syntax

To run this command outside of HCK Studio, you must stop the Smart Card service, run the command, and then the start the Smart Card service.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Command</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ifdtest2.exe -sa -sb -sc -se -sf</strong></p></td>
<td><p>Runs the test.</p></td>
</tr>
</tbody>
</table>

 

### File list

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ifdtest2.exe</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\nttest\Driverstest\storage\wdk\</p></td>
</tr>
</tbody>
</table>

 

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20Ifdtest2%20Part%20D%20%28SC%20Reader%20LOGO%29%20-%20%28Manual%20Test%29%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



