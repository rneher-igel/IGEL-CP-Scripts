# Building IGEL OS Custom Partition

## Summary of steps to create custom partitions

| Step | Description |
|------|-------------|
| 1. |Setup lab environment|
| 2. |Download Linux package|
| 3. |Unpack the package on a Linux system|
| 4. |Create the initialization script|
| 5. |Compress the custom partition contents|
| 6. |Write the \*.inf Metadata file|
| 7. |Upload the files to the UMS|
| 8. |Create a UMS profile for the custom partition|
| 9. |Assign the profile, check for missing libraries, and test the application|

See the following:<br />
[IGEL KB Document: Custom Partition Tutorial](https://kb.igel.com/igelos-11.03.500/en/custom-partition-tutorial-27245326.html)
<br />
[How to Install Microsoft Teams in a Custom Partition on IGEL OS - White Paper](https://www.igelcommunity.com/post/how-to-install-microsoft-teams-in-a-custom-partition-on-igel-os-white-paper)

## Finding and adding missing shared libraries

Find the missing libraries on the IGEL OS.

On IGEL OS:
```{find missing shared libraries}
cd /custom/zoom
find . -executable -type f -exec ldd ‘{}’ \; | grep ‘not found’ >> /custom/ldd.txt
  ```

On Linux Ubuntu:
```{download missing libraries and add to CP}
apt download <filename>
dpkg -x <filename>.deb zoom
  ```

To seach for missing libraries to download:  https://packages.ubuntu.com/bionic/allpackages


## Vendors

|  Vendor Name |
|--------------|
| [Microsoft](./Microsoft)|
| [Zoom](./Zoom)|

## How-to use a Custom Partition

### General
------------------------------------
IGEL custom partitions are delivered as a zip archive. The archive has the following content:

| Folder | Description |
|--------|-------------|
|igel | folder containing UMS profiles|
|target | folder containing Custom Partition (inf and tar.bz2 files)|
|disclaimer.txt | disclaimer note|
|readme.txt | Short Installation guide|

### Steps to deploy the Custom Partition
------------------------------------

| Step | Description |
|------|-------------|
| 1. | Copy the contents of the folder target into the ums_filetransfer folder on the UMS Server|
| 2. |Check the accessibility of the data using Internet browser: <br /> https://<ums_server>:8443/ums_filetransfer/cpname.inf |
| 3. |Import the profile (profiles.zip) into the UMS via: <br /> "System->Import->Import Profiles" <br /> The imported profile should now appear in UMS under Profiles.|
| 4. |Edit the profile and adopt the settings according to your environment via: <br /> System->Firmware Customization->Custom Partition->Download <br /> a. https://<ums_server>:8443/ums_filetransfer/<cpname>.inf <br /> b. Username: \<ums-username> <br /> c. Password: \<ums-password>
|5. |Assign the profile and files to IGEL device(s).|
|6. |In some cases it is required to restart the TC after deployment of the CP.|

## IGEL Disclaimer

The provided packages for use with the IGEL OS Custom Partition feature are without any warranty or support by IGEL Technology.
<br /> <br />
The files are not designed for production usage, use at your own risk. IGEL Technology will not provide any packages for production use and will not create or support any other packages or the implementation for other 3rd party software.
<br /> <br />
IGEL Technology is not responsible for any license violation created with the custom partition technology or the provided technical demonstation packages.
<br /> <br />
The custom partition technology can create a permanent damage in the IGEL OS host system, services related to the wrong usage/misinstallation of a custom partition and/or the deployed packages are not covered by the warranty in any kind.
<br /> <br />
You will not get support as long the custom partition is used on a system, to avoid conflicts you've to reset the device back to factory defaults before opening a support call.
<br /> <br />
All packages are designed as technical demonstration samples!
<br /> <br />
Use at your own risk!
<br /> <br />
Your IGEL Support/PreSales Team April 2012
