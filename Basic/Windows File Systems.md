Windows File Systems

# Windows File Systems

## File System
1. **FAT** (File Allocation Table)- Limits number of entries in the root directory. Has cluster issues.  
2. **NTFS** (New Technology File System) - It has data structure overhead and cluster issues. 
3. **ExFAT** (Extended File Allocation Table)- It has limited support outside Win/MacOS. Difficult to obtain. 
4. ReFS (Resilient File System) - This is new for Windows Server 2012 
* * *
## Access Control List
1. **DACL** (Discretionary Access Control List)- Allows or denies a user access to a file. Identifies the group permissions. 
2. **SACL** (System Access Control List) - Logs attempts to access a file. 

### Permission types of an ACL 
Full Control. Modify. Read and Execute. Read. Write. 

* * *
## Permissions

#### Inherited permissions 
Permissions assigned by Windows that are attained from a parent object. 

#### Explicit Permissions 
Permissions granted directly to a file or folder. 

 