# Working with Patch files 

## Tools:
     diff command
     patch command

- To compare two files, use `diff` command. For example,
           `diff <file1_name> <file2_name>`

  meaning of stdout (standard output on terminal) information for `diff` command:
  ```
        c - replace content of the line
        a - append 
        d - delete
        < - remove character after the sign
        > - characters after the sign should be added
  ```
- To compare contents of directories

        diff -r <directory1_name> <directory2_name>

- To copy output of a `diff` command to a patch file, use the following command

        diff <file1_name> <file2_name>  > patchfile.patch

  For example: making a patch file from changes in two Python codes

        diff original.py udpate.py > patchfile.patch

- Applying a patch file

        patch <name_of_file_to_patch> -i <patchfile> -o <file_name_to_generate_after_applying_patch>
    
    Note: 
     - applying a patch file should be done in a different directory to prevent conflict between the file generate after patching and file from which patch was created from.

     - check difference between a newly created (udpated) file and original (file used to create patch) file. There should be no difference.

         ` diff <original_file> <updated_file> `

- Applying a patch file without creating a new file

       method 1: before executing command, copy file to be patched and patchfile to the same directory
            patch -i patchfile.patch     
       
       method 2:  use p0 or p1 to specify path of file to be patched
            patch -p<0-9> -i patchfile.patch  

- Reverse effect of patching

        patch -p<0-9> -R -i patchfile.patch


  
