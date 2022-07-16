## linux

Linux Distribution

* [linux documentation](https://linux.die.net/)
* [linux directory structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

### move cursor

* ctrl + a: move cursor to start of line
* ctrl + e: move cursor to end of line
* ctrl + u: delete line where cursor at

### common linux command

> [101 Bash Command and Tips for Beginner to Experts](https://dev.to/awwsmm/101-bash-commands-and-tips-for-beginners-to-experts-30je#the-basics)

* ls
* ln
  * -s
* mkdir
  * -p: permit create directories recursively
* find
* grep
* gzip
* [tar](https://en.wikipedia.org/wiki/Tar_(computing))
  * `tar -cvf book.tar book`
  * `tar -xvf book.tar book`
  * -c: create: Create a new archive containing the specified items
  * -x: extract:  Extract to disk from the archive
  * -f: file: Read the archive from or write the archive to the specified file
  * -z: --gunzip, --gzip: Compress the resulting archive with gzip

gzip vs tar:

```shell
tar -zcvf book.tar.gz book
tar -zxvf book.tar.gz book
```

* gzip can only compress files, not directory
* tar can create new archive from specified items, it without compression feature
* xxx.tar.gz: first gzip then tar

look file(large file):

* cat
* more
* head
* tail

operator:

* | : pipe operator

```shell
head -6 report.html | tail -3
```

Disk Usage, Processes:

* df
* du
* ps
* top
* kill

#### environment variables

echo $PATH

immediately work after change environment variables config file:

* source `configFile`
* . `configFile`

environment variable config files:

* `/etc/profile`
* `/etc/bashrc`
* `~/.bash_profile`
* `~/.bashrc`

read files content which listed above

#### user and user group

* file `/etc/group`: store user group information
  * `root:x:0:root`
  * root: name of user group
  * x: password placeholder
  * 0: number of user group
  * root: username list of group

### file permission

> [Understanding Linux File Permission](https://linuxize.com/post/understanding-linux-file-permissions/)

```shell
ls -l
```

```text
-rw-r--r-- 12 linuxize users 12.0K Apr  28 10:10 file_name
|[-][-][-]-   [------] [---]
| |  |  | |      |       |
| |  |  | |      |       +-----------> 7. Group
| |  |  | |      +-------------------> 6. Owner
| |  |  | +--------------------------> 5. Alternate Access Method
| |  |  +----------------------------> 4. Others Permissions
| |  +-------------------------------> 3. Group Permissions
| +----------------------------------> 2. Owner Permissions
+------------------------------------> 1. File Type
```

File:

* `-` : regular file
* `d` : directory
* `l` : symbolic link

permissions:

* r(read): 4
* w(write): 2
* x(execute): 1
* no permission: 0
* rwx=4+2+1=7

[Symbolic(Text) Method](https://linuxize.com/post/understanding-linux-file-permissions/#symbolic-text-method):

```shell
chmod u=rwx,g=r,o= filename
```

[Numeric Method:](https://linuxize.com/post/understanding-linux-file-permissions/#numeric-method)

```shell
chmod 644 dirname
```

directory: no `x` permission, go into directory will tip permission denied

execute a file:

* first own execute permission
* `./2.txt`, `sh ./2.txt` (file content: `echo hello`)

### Operator

* declare
* set
* export

### some

* awk
* sed
* sort

timed task:

* crontab

### service

* RPM
* source

packet manager

* yum

