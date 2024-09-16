# DevOps dex curse Bank Hapoalim
DevOps curse

# PART 1 INSTALLATION VM solution Part 1: VirtualBox & Ubuntu Installation

![image](https://github.com/user-attachments/assets/48b56046-0828-467e-9b2e-a806c58cd7a2)


# Linux File Creation, and Command Usage 

### Part 2: Linux Directory and File Creation ** SCREENSHOT FOR ALL PART HOMEWORK at the end **

```bash
mkdir -p ~/homework/{dir1,dir2,dir3}
```

This command creates a directory structure with a main directory `homework` and three subdirectories `dir1`, `dir2`, and `dir3`.

- `mkdir`: Command to make directories
- `-p`: Creates parent directories if they don't exist
- `{}`: Brace expansion to create multiple directories in one command

### Creating Files

```bash
touch ~/homework/dir1/{file1.txt,file2.txt,file3.txt}
```

This command creates three empty text files in the `dir1` directory.

- `touch`: Command to create empty files or update timestamps of existing files
- `{}`: Brace expansion to create multiple files in one command

### Adding Content to Files

```bash
echo "This is the content of file1" > ~/homework/dir1/file1.txt
echo "This is the content of file2" > ~/homework/dir1/file2.txt
echo "This is the content of file3" > ~/homework/dir1/file3.txt
```

These commands add content to each file using the `echo` command and output redirection.

- `echo`: Prints text to the terminal
- `>`: Redirects output to a file, overwriting existing content

## Part 3: Using grep and find Commands

### grep Command

```bash
grep "vitaly" ~/homework/dir1/*.txt
```

This command searches for the word "content" in all `.txt` files in the `dir1` directory.

- `grep`: Command for searching text using patterns
- `*.txt`: Wildcard to match all `.txt` files
- 
  


```bash
grep -i "file1" ~/homework/dir1/*.txt
```

This command searches for "file1" in all `.txt` files, ignoring case.

- `-i`: Makes the search case-insensitive



### find Command

```bash
find ~/homework
```

This command lists all files and directories within the `homework` directory and its subdirectories.


```bash
find ~/homework -name "*.txt"
```

This command finds all `.txt` files in the `homework` directory and its subdirectories.

- `-name`: Allows specifying a pattern to match filenames

###  ** PART 3**



```bash
find ~/homework -type f -mtime -7
```

This command finds files modified within the last 7 days in the `homework` directory and its subdirectories.

- `-type f`: Specifies that we're looking for files (not directories)
- `-mtime -7`: Means "modified time less than 7 days ago"

![image](https://github.com/user-attachments/assets/ec3a7afb-0433-4161-b2cf-d0a6ff1bf247)


