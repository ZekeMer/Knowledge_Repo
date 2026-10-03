### **Information based on OverTheWire Games**



**ls \[options] —** List files.

* **-a —** Show all.
* **-A —** Show all; exclude "." and "..".



**du \[options] —** Estimate drive space taken by files and directories in 1024-byte blocks.

* **-h —** Display in human readable format.



**find \[path] \[options] \[expression] —** Used to search files and text strings based on file metadata (name, size, date, permissions, etc.).

* **-user \[user\_name] —** Search for files owned by the provided user.
* **-group \[group\_name] —** Search for files owned by the provided group.
* **-name —** Search for specific names. Case sensitive.
* **grep —** Combine with grep to search the contents of a file.
* **-type f —** This specific option searches only for regular files and ignores directoreies, symbolic links, device files, etc.
* **-size \[parameter] —** Search by size. Prepend a +/- to specify greater than or lesser than. Add another size with an accompanying parameter to search within a size range. To specify sizes, append the following values.

  * **c —** bytes
  * **k —** kilobytes
  * **M —** Megabytes
  * **G —** Gigabytes
* **Ex —**

  * **find ./\* -type f -size +1030c -size -1055c** — Search through everything in current directory for regular files within size range 1030-1055 bytes.



**file \[options] \[file] —** Determine file type by examining contents and metadata.

* **-b —** Exclude filename in output.



**Dashed Filenames —** Files which begin with dashes (- or --) cause issue in the terminal due to misinterpretation as flags/options. There are two ways this can be resolved.

* **Double Dash Separator:** Use "--" between the command and the file. The double dashes indicate the end to option parsing.
* **Path Prefixing:** Use a relative or absolute path to clear the confusion.



**Spaces in Filenames —** Spaces can be interpreted as command argument separators. There are 2 common methods to bypass this issue.

* **Quoting:** Quote the file name in the command. Use single quotes (') to treat the content literally and double quotes (") to allow for variable expressions.
* **Escaping —** Place a backslash directly before each space in the name to ignore them as command argument separators. The spaces are then treated literally.



The "**\***" does not include hidden files.



**grep \[options] \[pattern] \[file] —** Searches for patterns found in given file.

* **-v —** Excludes given pattern.



**The 3 I/O Streams** are predefined for each process in Unix/POSIX systems and are as follows.

* **stdin —** Descriptor\*\*: 0 —\*\* Used for reading terminal input. Defaults to keyboard input but is able to be redirected from a file, pipe (|), or other objects.
* **stdout —** Descriptor\*\*: 1 —\*\* Used for writing normal output to terminal for program results and data. It is the stream which gets piped (|) to other commands. ">" and "1>" redirect stdout to a file. "2>\&1" redirects both stdout and stderr together.
* **stderr —** Descriptor\*\*: 2 —\*\* Used to write diagnostics and errors to terminal. Separated to prevent errors and warnings in data outputs. Because it is a separate stream, stdout redirects can happen meanwhile stderr outputs still appear. "2>" redirects stderr to a file. "2>\&1" merges stderr into stdout.

Each is, by default, connected to the terminal.

* **Ex —**

  * **find / -type f -user bandit7 -group bandit6 -size 33c 2>\&1 | grep -v ":"**
  * **find / -type f -user bandit7 -group bandit6 -size 33c | grep -v ":"**
  * The two above commands are attempting to locate files with a specified user, group, and size. It then uses the collected data to exclude lines with a colon in them, which indicate errors have occurred. However, only the top command completely narrows down the file because it sends both stdout and stderr. The other find command only sends stdout through the pipe because that is what find defaults to sending.



**sort \[options] \[file] —** Sorts identical lines together.



**uniq \[options] \[file] —** Report or omit repeated lines. Only checks adjacent lines.

* **-i —** Ignore case differences.
* **-u —** Only print unique lines.
* **-w \[X] —** Compare no more than X characters in lines.
* **Ex —**

  * **sort filename.txt | uniq -u** — Sort filename.txt so all similar lines are adjacent. Then, find the unique line among the sorted output.



**strings \[options] \[file] —** Print sequences of printable characters in files. Defaults to sequences at least 4 characters long. Useful for determining the contents of non-text files.

* **-n \[minimum-lenn] —** Print sequences of characters of at least the specified minimum length.



**base64 \[options] \[file] —** Used to encode/decode data and print to standard output.

* **-d —** Decode data.
* **-i —** When decoding, ignore non-alphabetic characters.



**tr \[options] \[set1] \[set2] —** Translate or delete characters using sets. Set1 is the set to be replaced, as should map to set2, which contains the replacements. The command has no file parameter, data from a file must be output from or input into it (| or < = stdout or stdin).

* **Ex —**

  * **tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt** — Solving a ROT13 cipher (shifted 13 characters). Set1 indicates what needs to be replaced, in this case the entire upper and lower case alphabet. Since the sets must be positionally mapped, both sets have 52 characters (26 for each of the alpahbets lower and upper case). Set2's characters are shifted 13 down to account for the ROT13 cipher.



**tar \[options] \[file] —** An archiving utility originally made to read/write from/to tape drives.

* **-f —** This flag is often needed to indicate to tar which file to use as it defaults to the env variable TAPE.
* **-x —** Extracts archive.
* **-t —** View files within the archive without extracting.
* **-v —** Verbose for more detailed view of archive.



**gzip \[options] \[file] —** Used to compress or expand. Handles GZIP archives. May require file to end in ".gz".

* **-d —** Decompress file.
* **gunzip —** Separate command. By default, it decompresses.

  * **-c —** Decompress but only send to stdout.
* **zcat —** Separate command. By default, it decompresses files but only sends to stdout without changes to the file.



**bzip2 \[options] \[file] —** Compress and decompress files using the Burrows-Wheeler block sorting algorithm. May require file to end in ".bz2".

* **-d —** Force decompress.
* **-c —** Compress or decompress to stdout.



**xxd \[options] \[infile] \[outfile] —** Used to create or reverse hexdumps. uses infile and outfile fields for inputted and exported destination file.

* **-r —** Revert hexdumps to binary. If not to stdout, writes to outfile.



**mv \[options] \[file] \[destination/new\_file\_name] —** Used to move or rename files.



