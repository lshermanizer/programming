## Wildcard

https://superuser.com/questions/1124790/delete-files-with-wildcard-in-subfolder

The DEL command in your example should be in this syntax:
```
DEL /Q /F /S "*.tmp"
```
Essentially you don't need to try to wildcard any folder paths and the /S switch is used to delete specified files from all subdirectories from the directory you are in when you run the command and all the way down recursively from all beneath subfolders.
