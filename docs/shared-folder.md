# JupyterHub Shared Folder

On request, it's possible to set up a shared folder in JupyterHub. However, this is not done by default, as managing permissions in the shared folder will require ongoing work from teaching staff in a course. Managing files in the shared folder will require the use of the terminal in JupyterHub, and users will benefit from general knowledge of Unix filesystem permissions.

If you're already familiar with setting file permissions in a Unix system, here is some information about the setup so you can manage it. There is a group with gid 3000 called `teachingstaff` that course instructors and TAs/TFs are included in. This is the group owner of the `course_data` folder located at `/home/course_data`, parallel with user home folders. JupyterHub sets a default `umask 0077`, so permissions will be 600 or 700 by default. For use in courses, we recommend group read/write access and global read access, so 664 or 775. File owners can use chmod commands to modify permissions appropriately.

## Creating Files with Appropriate Permissions

Since JupyterHub is configured with a shared file system, JupyterHub is configured to ensure that new files that are created are only accessible by the creator of that file. It does this with the use of a `umask`, which sets the default permissions of newly created files. The default is to create files with no access other than by the file owner.

To change this default in order to create files that are accessible by other users, it's necessary to change the umask. A command that will change the `umask` for adding files to the shared folder is `umask 0002`. After this command is run, all files created in that terminal session will give read/write access to the owner and the group owner (the teaching staff group in the shared folder), and global read access so students can have read-only access to shared files.

The `umask` command only affects the terminal, and only affects the terminal session in which it was run. If you close the terminal and start a new one, you will need to run `umask 0002` again before the default permissions will be set appropriately.

## Fixing Permissions on Existing Files

For files that were created outside of the terminal, or in the case of files that were created when the `umask` was set at the default value, file and folder owners can change the permissions to open them up to provide read/write access to teaching staff. The following commands should fix permissions when run from `/home/course_data`:

```bash
# Grant read/write access to the group owner
chmod -R g+rw .
# Grant read access globally so students can read files
chmod -R o+r .
# Ensure that folders work properly for everyone
chmod -R go+X .
```
