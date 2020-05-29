- [Strings]()
- [Files]()
- [Directories]()
- [System porcesses]()
- [IP addresses]()
- [Networking]()

### Strings

> `echo string_you_want_to_encode | base64`
- Encode string in base64

### Files

> `find / -name <file_name>`
- Find <file_name> from root

> `chmod +x <file_name>`
- Make <file_name> executable

> `content | tee <file_name>`
- Output content to <file_name>

> `echo <content> > <file_name>`
- Create <file_name> with <content>

> `echo <content> >> <file_name>`
- Append <content> in <file_name>

> `cat|tail|less|more <file_name>`

### Directories

> `mkdir -p <existed_directories/parent_directory/child_directory>`

### System processes

> `ps aux`
- ps: processes status from /proc file
- a = show processes for all users
- u = display the process's user/owner
- x = also show processes not attached to a terminal

> `grep Cap /proc/<PID>/status`
- See the [linux capabilities](https://github.com/torvalds/linux/blob/master/include/uapi/linux/capability.h) of the process with <PID>

> `capsh --decode=<capabilities>`
- Decode the linux capabilities

### IPs

> `curl ifconfig.me`
- Get the IP address of the local machine

### Networking

> `nc` <IP> <port> (Netcat)
- v: verbose mode
- z: scan for listening daemons, without actually sending any data to them
- w: specifies a timeout for connection that can not be established
