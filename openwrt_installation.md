## How to install a package on OpenWrt router

### First Approach
- Download all necessary dependencies

- Ensure that the package to install has its own Makefile. For example, the Makefile is usually located at ``<source_home>/package/<package_name>/Makefile``

- Inside OpenWrt home directory, issue the following commands
```
    make tools/install
    make toolchain/install
```

- Build package
```
    make  package/<package_name>/compile
```

- Install package
   1. If compilation and installation are done on the same computer or router*, enter command below
        ``` 
        make package/<package_name>/install
        ```        
   2. If installation is on a different computer or router*,
        - copy to desired destination        
            ``` 
            scp <source_directory_with_compiled_package> <dest_directory_to_install_package>
            ```
             Example: ``scp BUILD_DIR/bin/ar71xx/package/<file_name>.ipk  root@192.168.1.1:/~ ``

        - SSH to the destination directory on access point or router*  with OpenWrt. For example,
           ```
           ssh  <username>@<router_address>; 
           ```
            Example: ``ssh root@192.168.1.1``
        - Change directory to location where the file is copied
        - Install package by typing command below on the terminal.
            ```
             opkg install ./<file_name>.ipk
            ```
        - To confirm package installation, type command below at the terminal
            ```
             opkg list | grep <package_name>
            ```
### Second Approach
- Connect access point or router* to a computer using LAN (Ethernet) port

- Connect to Internet via the WAN port on the router*

- SSH into the router*
   ```
    ssh  <username>@<router_address>; 
   ```
   Example: ``ssh root@192.168.1.1``
- On the router's terminal, enter the following commands
    ```
    $ opkg update
    $ opkg install <package_name>
    ```
- Verify installation using command
    ```
    $ opkg list | grep <package_name>
    ```





\* A router is a commodity device that functions both as an access point and a router. This should not be
confused with an enterprise router or gateway


### References
1. https://oldwiki.archive.openwrt.org/doc/devel/packages
2. https://oldwiki.archive.openwrt.org/doc/techref/opkg
3. https://oldwiki.archive.openwrt.org/doc/howto/buildroot.exigence
