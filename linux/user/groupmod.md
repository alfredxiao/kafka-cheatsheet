# Rename
* `groupmod -n new_name old_name`
- files owned by 'old_name' will now be owned by 'new_name' as this is by GID which remains the same

# Change group id
- `groupmod -g new_id groupname`
* all files that were associated with that group will no longer be associated with any group name. Instead, these files will be owned by a GID only
  * These files with no group name are called orphaned files
* To search for all files that are owned by just a GID (not associated with a group name) use the -nogroup option of the find command:
  * `find / -nogroup`
