
### Basic Password Files
- SAM and SYSTEM File DIrectory - `C:/windows/system32/config/` 
- Get hashs from SAM and SYSTEM FILE - `Impact-secretsdump --sam SAM –system SYSTEM` 
- Empty Password: - `31d6c......` 

### Hash Cracking
```bash 
john ~/temp/hash.txt  2020-200_most_used_passwords.txt
```
 
 ### Create wordlist
 ```bash
 cewl -w cewl_passlist.txt -d 5 10.11.1.39/otrs/index.pl
 ```