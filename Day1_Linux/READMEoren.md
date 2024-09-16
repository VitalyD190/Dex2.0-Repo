# DevOps dex curse Bank Hapoalim
DevOps curse

# PART 1 INSTALLATION VM solution Part 1: VirtualBox & Ubuntu Installation

![image](https://github.com/user-attachments/assets/b105b835-2078-44a9-aace-0728ede085aa)

![image](https://github.com/user-attachments/assets/2e147a9d-5e18-45dc-a5f7-e646951cfc9c)

![image](https://github.com/user-attachments/assets/2bafdc26-f439-4ce8-8a0f-67b1445f4b8e)

![image](https://github.com/user-attachments/assets/ea137514-c2da-46f9-8254-69fad91e1e95)


# Linux File Creation, and Command Usage 

### Part 2: Linux Directory and File Creation ** SCREENSHOT FOR ALL PART 2**

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
grep "Harari" ~/homework/dir1/*.txt
```

This command searches for the word "content" in all `.txt` files in the `dir1` directory.

- `grep`: Command for searching text using patterns
- `*.txt`: Wildcard to match all `.txt` files
- 
  
![image](https://github.com/user-attachments/assets/ae4df146-347a-4feb-a7cc-58ffa88ac6a2)

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

###  **THIS SCREENSHOT FOR ALL PART 3**

![image](https://github.com/user-attachments/assets/5ea03e93-e366-4eab-bf0c-6fed53320401)


```bash
find ~/homework -type f -mtime -7
```

This command finds files modified within the last 7 days in the `homework` directory and its subdirectories.

- `-type f`: Specifies that we're looking for files (not directories)
- `-mtime -7`: Means "modified time less than 7 days ago"

[Screenshot of find command for recently modified files and output]


Part 4: Documenting the Steps at this readme.md file :) 
