The letters represent:

    r: Read permissions. The file can be opened, and its content viewed.
    w: Write permissions. The file can be edited, modified, and deleted.
    x: Execute permissions. If the file is a script or a program, it can be run (executed).


For example:

     --- means no permissions have been granted at all.
     rwx means full permissions have been granted. The read, write, and execute indicators are all present.


Values we can use are:

    u: User, meaning the owner of the file.
    g: Group, meaning members of the group the file belongs to.
    o: Others, meaning people not governed by the u and g permissions.
    a: All, meaning all of the above.

    –: Minus sign. Removes the permission.
    +: Plus sign. Grants the permission. The permission is added to the existing permissions. If you want to have this permission and only this permission set, use the = option, described below.

    r:  The read permission.
    w: The write permission.
    x: The execute permission.

Examples:

    chmod u=rw,og=r new_file.txt
    chmod a+x new_script.sh
    chmod o-r *.page
    chmod -R o-r *.page


The digits you can use and what they represent are listed here:

    0: (000) No permission.
    1: (001) Execute permission.
    2: (010) Write permission.
    3: (011) Write and execute permissions.
    4: (100) Read permission.
    5: (101) Read and execute permissions.
    6: (110) Read and write permissions.
    7: (111) Read, write, and execute permissions.


Example:

    chmod 664 *.page


	
--------------------------------


To remove executable bit from all txt files under a directory (first we need to tell our shell the new line character is \n as if not it will fail with txt files containing spaces in their names and would cause major problems on some files):

    $ export IFS=$'\n'
    $ for i in `find ~/Documents/oposRelated -name '*.txt' -type f`; do chmod -x $i; done


