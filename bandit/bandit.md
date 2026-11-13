# OverTheWire Bandit

## Level 0 -> 1
- **Goal:** find the password stored in a file called `readme`
- **Commands:** `ls`, `cat readme`
- **Learned:** ssh uses `-p` to pick a non-default port

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
