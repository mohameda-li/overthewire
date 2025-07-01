## Level 0 ➜ 1
**Goal:** The password for the next level is stored in a file called `readme` located in the home directory. Use this password to log into `bandit1` using SSH on port 2220.
**Steps:**
```bash
cat readme
```
**Password:** `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

## Level 1 ➜ 2
**Goal:** The password for the next level is stored in a file called `-` located in the home directory.
**Steps:**
```bash
cat ./-
```
**Password:** `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

## Level 2 ➜ 3
**Goal:** The password for the next level is stored in a file called `spaces in this filename` located in the home directory.
**Steps:**
```bash
cat "spaces in this filename"
```
**Password:** `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

## Level 3 ➜ 4
**Goal:** The password for the next level is stored in a hidden file in the `inhere` directory.
**Steps:**
```bash
cd inhere
ls -a
cat .hidden
```
**Password:** `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

## Level 4 ➜ 5
**Goal:** The password for the next level is stored in the only human-readable file in the `inhere` directory.
**Steps:**
```bash
cd inhere
file *
cat <human-readable-file>
```
**Password:** `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

## Level 5 ➜ 6
**Goal:** The password for the next level is stored in a file somewhere under the `inhere` directory and has all of the following properties:
- human-readable
- 1033 bytes in size
- not executable
**Steps:**
```bash
find inhere -type f -size 1033c ! -executable
cat <found-file>
```
**Password:** `HWasnPhtq9AVKe0dmk45nxy20cvUa6E`

## Level 6 ➜ 7
**Goal:** The password for the next level is stored somewhere on the server and has all of the following properties:
- owned by user `bandit7`
- owned by group `bandit6`
- 33 bytes in size
**Steps:**
```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
**Password:** `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

## Level 7 ➜ 8
**Goal:** The password for the next level is stored in the file `data.txt` next to the word `millionth`.
**Steps:**
```bash
grep millionth data.txt
```
**Password:** `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

## Level 8 ➜ 9
**Goal:** The password for the next level is stored in the file `data.txt` and is the only line of text that occurs only once.
**Steps:**
```bash
sort data.txt | uniq -u
```
**Password:** `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

## Level 9 ➜ 10
**Goal:** The password for the next level is stored in the file `data.txt` in one of the few human-readable strings, preceded by several ‘=’ characters.
**Steps:**
```bash
strings data.txt | grep '='
```
**Password:** `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

## Level 10 ➜ 11
**Goal:** The password for the next level is stored in the file `data.txt`, which contains base64 encoded data.
**Steps:**
```bash
base64 --decode data.txt
```
**Password:** `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

## Level 11 ➜ 12
**Goal:** The password for the next level is stored in the file `data.txt`, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.
**Steps:**
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
**Password:** `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

## Level 12 ➜ 13
**Goal:** The password for the next level is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed. For this level, it may be useful to create a directory under `/tmp` in which you can work.
**Steps:**
```bash
xxd -r data.txt > data.bin
mktemp -d
cd /tmp/<your-dir>
cp data.bin /tmp/<your-dir>
file data.bin
# Use mv to allocate the correct suffix to the file
# Use guzip, buzip2, tar etc. repeatedly to unpack
# Once the file is ascii use the cat command
```
**Password:** `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

## Level 13 ➜ 14
**Goal:** The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`. You get a private SSH key that can be used to log into the next level.
**Steps:**
```bash
chmod 600 sshkey.private
ssh -i sshkey.private bandit14@localhost -p 2220
# Now we are in bandit14
cat /etc/bandit_pass/bandit14
The password is: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```
**Password:** `MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`

## Level 14 ➜ 15
**Goal:** The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
**Steps:**
```bash
echo "MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS" | nc localhost 30000
```
**Password:** `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`
