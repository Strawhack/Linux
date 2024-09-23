
```ruby
Python3
$python3 -c 'import pty; pty.spawn("/bin/bash")'

Python2
$python2 -c 'import pty; pty.spawn("/bin/bash")'

Script
$script /dev/null -qc /bin/bash

Others
$echo os.system('/bin/bash')
$/bin/sh -i

Perl
$perl -e 'exec "/bin/sh";'
$exec "/bin/sh";

Ruby
$exec "/bin/sh"

Lua
$lua -e "os.execute('/bin/sh')"
```
