# OverTheWire Bandit

## Level 0 -> 1
- **Goal:** find the password stored in a file called `readme`
- **Commands:** `ls`, `cat readme`
- **Learned:** `ssh` uses `-p` to pick a non-default port.

## Level 1 -> 2
- **Goal:** find the password stored in a file called `-`
- **Commands:** `ls`, `cat ./-`
- **Learned:** I didn't know what dashed filenames meant. I tried `cat -` and `nano -` but it didn't work, because commands treat `-` as a special argument (stdin), not as a filename. Adding a path like `./` before the name fixes it.

## Level 2 -> 3
- **Goal:** find the password stored in a file called `--spaces in this filename--`
- **Commands:** `ls`, `cat ./"--spaces in this filename--"`
- **Learned:** This was the most painful so far. I always hated spaces in filenames on Linux. Quotes handle the spaces, but the name starts with `--`, so `cat` reads it as an option. Adding `./` before the name solves it.

## Level 3 -> 4
- **Goal:** find the password stored in a hidden file
- **Commands:** `cd`, `ls -a`, `cat ./`
- **Learned:** I learned a lot in this level. Now I understand how to list all files in a directory, including hidden files, using `ls -a`. Files starting with `.` are hidden. I also understand the difference between `~/` (home directory) and `./` (current directory).

## Level 4 -> 5
- **Goal:** find the password stored in the only human-readable file
- **Commands:** `cd`, `ls -a`, `file`, `cat ./`, `find`
- **Learned:** This level was tricky because there are many paths to the solution. I used `file ./-filename` to find the human-readable file, but you can also use `file ./*` or `find` with pipes: `find ./ -type f | xargs file | grep text`.

## Level 5 -> 6
- **Goal:** find the password stored somewhere under the `inhere` directory that has all the following properties: human-readable, 1033 bytes in size, not executable
- **Commands:** `cd`, `ls -a`, `find ./ -type f -size 1033c ! -executable`, `cat`, `man find`
- **Learned:** This level was the hardest so far. I didn't know the syntax of `find` well, so `man find` was really useful (alternatives that are easier to read: `find --help`, `tldr find`, `curl cheat.sh/find`). Things I learned about `find`:
  - `./` is the starting point, and `find` also searches all subdirectories.
  - `-type f` means regular file (`d` = directory, `l` = symlink).
  - `-size 1033c` means exactly 1033 bytes. The `c` stands for bytes; without it the number is counted in 512-byte blocks.
  - `!` (or `-not`) negates the next condition, so `! -executable` excludes executable files.
  - All conditions go together in the same command, separated by spaces, with an implicit AND between them. They are options of `find`, not separate commands, so they never go after a pipe `|`. A pipe is only for sending the output of `find` to another command (like `file`).

## Level 6 -> 7
- **Goal:** find the password stored somewhere on the server that has all the following properties: owned by user bandit7, owned by group bandit6, 33 bytes in size
- **Commands:** `find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null`, `cat`, `id`
- **Learned:** This level was easier than I expected, but I overcomplicated it.
  - **Searching the whole server:** the file can be anywhere, so the search starts at `/` (root), the parent of all directories. That's different from `~/` (my home directory, `/home/bandit6`) and `./` (the current working directory).
  - **User and group IDs:** I thought I needed the numeric IDs. `id` and `id -u` only show the IDs of the current user, so I searched on Stack Overflow and used `awk -F: '/\/home/ {printf "%s:%s\n",$1,$3}' /etc/passwd`. All of this for nothing: `find` accepts names directly (`-user bandit7 -group bandit6`). If I ever need another user's ID, `id bandit7` or `grep bandit7 /etc/passwd` are simpler.
  - **What that `awk` command does:** `/etc/passwd` is the file where Linux keeps the list of users. Each line is a user, with fields separated by `:` (name:x:UID:GID:...:home:shell). `awk -F:` splits each line using `:` as a separator, `/\/home/` keeps only the lines that contain `/home`, and `printf "%s:%s\n",$1,$3` prints field 1 (name) and field 3 (UID).
  - **`2>/dev/null`:** searching the whole server prints hundreds of `Permission denied` errors. In Linux each command has two output channels: 1 (stdout) for normal results and 2 (stderr) for errors. `>` means "redirect to", and `/dev/null` is a special file that works as a trash can: everything sent there disappears. So `2>/dev/null` means "send all errors to the trash".
  - **My mistake:** I first wrote `find ... | 2>/dev/null`. That's wrong because `2>/dev/null` is not a command, it's a redirection for the command it's attached to. With the pipe, the normal results got lost and the errors still showed up (the opposite of what I wanted). It goes at the end of the command, without `|`.
  - **`|` vs `>`:** `|` connects the output of one command to another command. `>` sends an output to a file.

## Level 7 -> 8
- **Goal:** find the password stored in the file `data.txt` next to the word millionth
- **Commands:** `ls`, `grep millionth data.txt`
- **Learned:** This was pretty easy, but I managed to overcomplicate it. First I tried `grep password data.txt` and it matched three lines (`passwords`, `password's`, `password`), but those passwords were fake. I didn't read the instructions well; I just had to grep the word `millionth`. `grep` matches any line that *contains* the text, even inside a longer word. `grep -w password data.txt` only matches the whole word, which is useful when a file has similar words.

## Level 8 -> 9
- **Goal:** find the password stored in the file `data.txt`; it is the only line of text that occurs only once
- **Commands:** `ls`, `sort data.txt | uniq -u`
- **Learned:** Honestly, I hated this one because I didn't understand the logic of `uniq` and `sort`. I'll try to explain it the best I can.
  - `sort` prints the lines of a file in a particular order (alphabetically by default). Like `cat`, it does not modify the file; the difference is that `cat` prints the lines as they are saved, and `sort` prints them ordered.
  - `uniq` detects, reports or removes duplicate lines, **but only adjacent ones**: it compares each line with the one right above it and doesn't remember anything else.
  - Why not just `sort -u` or `uniq -u`? Let's see with an example.

Imagine a text file that contains:

```
aaa  <--- repeated
bbb  <--- repeated
aaa  <--- repeated
bbb  <--- repeated
ccc  <--- repeated
ddd  <--- once
ccc  <--- repeated
```

**`sort -u file.txt`** gives us:

```
aaa
bbb
ccc
ddd
```

It sorts the lines and keeps **one copy of each line**. That is not the same as "lines that occur only once": after this, we can't tell anymore that `aaa`, `bbb` and `ccc` were repeated. So it doesn't help us find the password.

**`uniq -u file.txt`** (unsorted) gives us all 7 lines, which is even worse. Why? Because the repeated lines are never next to each other. When `uniq` reaches the second `aaa`, it only compares it with `bbb` (the line above), so for `uniq` every line looks unique.

Now the same file sorted with **`sort`**:

```
aaa  <--- repeated
aaa  <--- repeated
bbb  <--- repeated
bbb  <--- repeated
ccc  <--- repeated
ccc  <--- repeated
ddd  <--- once
```

Now the duplicates are grouped together, so `uniq` can finally detect them:
- `uniq` (no option) keeps one copy of each line: `aaa`, `bbb`, `ccc`, `ddd` (same result as `sort -u`).
- `uniq -u` shows only the lines that were never repeated:

```
aaa  <--- deleted
aaa  <--- deleted
bbb  <--- deleted
bbb  <--- deleted
ccc  <--- deleted
ccc  <--- deleted
ddd  <--- finally!
```

So `sort` doesn't matter here because of the alphabetical order itself; it matters because it puts the identical lines next to each other so `uniq` can see them. That's why the solution is `sort data.txt | uniq -u`.

**My first attempt** was `sort -u data.txt | uniq -u data.txt`, and it had two mistakes:
1. `sort -u` removed the duplicates before `uniq` could see which lines were repeated.
2. Giving `data.txt` to `uniq` made it ignore the pipe and read the original unsorted file. When a command receives input from a pipe, don't give it a filename.

**Extra:** while testing with my own file in nano, `ccc` showed up twice with `sort -u`. One of the lines had an invisible trailing space (`ccc ` vs `ccc`). `cat -A file.txt` shows hidden characters (`$` marks the end of each line). Computers compare character by character: a space, a tab or an uppercase letter makes two lines different.

**Bonus:** `sort | uniq -c` counts how many times each line appears. This is useful for analyzing logs, for example counting requests per IP.

## Level 9 -> 10
- **Goal:** find the password stored in the binary file `data.txt`, in one of the few human-readable strings, preceded by several `=` characters
- **Commands:** `ls`, `cat`, `strings`, `grep`, `strings data.txt | grep "="`
- **Learned:** This one was pretty fun. My first try was using `grep` with `=` as the pattern, but it failed with the message `binary file matches`: `grep` detected that the file is binary and didn't print the lines. Then I tried `cat` and it worked, but the output was full of binary garbage mixed with the password. So I went further: `strings` extracts only the human-readable text from a binary file, and piping it to `grep` found the password.
  - **Possible improvements:** search for several `=` in a row (the level says "preceded by several `=` characters"), for example `strings data.txt | grep "==="`, to filter out the strings that only have one. Another option is `grep -a "===" data.txt`: `-a` tells `grep` to treat a binary file as text.

## Level 10 -> 11
- **Goal:** find the password stored in the file `data.txt`, which contains base64 encoded data
- **Commands:** `ls`, `cat`, `base64 --decode data.txt`, `echo <text> | base64 --decode`
- **Learned:** This level was easy, but I learned a lot of things I will definitely use in the future.
  - **Encoding ≠ encryption.** They sound similar but they're not the same. Encoding doesn't need a key, anyone can reverse it, and it's used to transport data. Encryption needs a key, only whoever has the key can reverse it, and it's used to protect data.
  - **What Base64 is:** a way to write any data (text, images, binaries) using only 64 "safe" characters: `A-Z`, `a-z`, `0-9`, `+` and `/`. It exists because some systems, like email or URLs, only support simple text, so you can send a file or an image as if it were text. It doesn't hide anything: it's like writing something in another alphabet that everybody knows.
  - **How to recognize it at first glance:** it only uses those 64 characters, and it often ends with `=` or `==` (padding added at the end, not always present). The file in this level ended in `Cg==`.
  - **Mistake I noticed:** running `base64 data.txt` without `--decode` doesn't decode anything, it encodes the data again (Base64 of Base64). That's why the output was longer and different.
- **Why this matters in cybersecurity:** Base64 is often used to disguise things. Attackers hide malicious commands in Base64 (for example, PowerShell with `-enc`) so they aren't readable at first glance in the logs, and SOC analysts decode them all the time. It also shows up in login tokens, HTTP headers and emails.
