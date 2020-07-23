# Building Custom Partition Scripts

## Summary of steps to create custom partitions

•	Setup lab environment <br />
•	Download Linux package <br />
•	Unpack the package on a Linux system <br />
•	Create the initialization script <br />
•	Compress the custom partition contents <br />
•	Write the \*.inf Metadata file <br />
•	Upload the files to the UMS <br />
•	Create a UMS profile for the custom partition <br />
•	Assign the profile, check for missing libraries, and test the application


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
