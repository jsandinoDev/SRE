# Linux Commands

### Basics

```

pwd            --> current dir

ls             --> list

ls -al         --> list all (hidden && not hidden)

ls -a          --> list hidden

ls -l          --> list not hidden

```

```

touch "file"            --> create file

cp file.txt file2.      --> copy file

cp -r /dir /dir2        --> copy dit

mv file.txt file2.txt   --> move file

mv /dir /dir2           --> move dit

mv -v /dir /dir2        --> -v more explicit

rm -rf dir1/            --> remove with content

```

### Pelado Linux

```
ls  -alh                --> list all files human readable

cp -a dir1/ dir2/       --> -a (archive) usefull when copy dirs

mv file.txt dir/        --> move file from pwd to target /dir

rsync -av dir1/ dir2/   --> if file exist dont copy

> file.txt              --> same as touch
```

```
du -sh /var/lib           --> show use of disk

du -sh /var/lib*          --> show weigth of each file

stat file.txt             --> show file info

zip -r images.zip images  --> zip file/folder

unzip images.zip          --> unzip

zipinfo images.zip        --> see content without unzip

```

```
tree                       --> show all files in a tree format

find . -mtime +5           --> find in current dir (.) -mtime(modified time) +5 days

find . -iname file*        --> find in current dir (.) -iname(name start with) file*

find . -iname file -delete --> find in current dir (.) -iname(name start with) file and -delete

cal                        --> show calendar

date                       --> show date

```

```
ps fax            --> show running process

kill PROCESSID    --> kill process

killall "name"    --> kill all process with one name

curl google.com   --> request http

curl ifconfig.me  --> show ippublic

```

```
cat file.txt                --> show file content

grep hola file.txt          --> filter file content

cat readme.txt | grep hola  --> cat + grep

grep -v                     --> contrary to grep

df -h                       --> show disk space

top                         --> show top running process

```

```
control + r                  --> show command history

netstat                      --> show net stats

netstat -nv                  --> show gateway stats

netstat -i                   --> show interfaces stats

netstat -natup               --> show process running tcp/udp

tcpdump                      --> scan red traffic

tcpdmump -i any host .....ip -->

```

```
locate                 --> search fiels

updatedb               --> update locate db

tail /dir/file.txt     --> show last 10 files

tail -f /dir/file.txt  --> show 10 last files and wait for new entry

ssh root@.....ip       --> connect to server

cat /proc/cpuinfo      --> show cpu stats

```

### SSH

```
apt-get install openssh-server  --> install ssh

systemctl enable ssh            --> enable shh

ssh root@....ip                 --> connect

ssh-key gen                     --> generate key

cat .ssh/id_rsa.pub             --> copy shh pub into server

vim .ssh/autorized-keys         --> copy in server


```
