**ls \[options] — List files.**

* **-a —** Show all.
* **-A —** Show all; exclude "." and "..".



**du \[options] —** Estimate drive space taken by files and directories in 1024-byte blocks.

* **-h —** Display in human readable format.



**find \[path] \[options] \[expression] —** Used to search files and text strings based on file metadata (name, size, date, permissions, etc.). 

* **-name —** Search for specific names. Case sensitive. 
* **grep —** Combine with grep to search the contents of a file.
* **-type f —** This specific option searches only for regular files and ignores directoreies, symbolic links, device files, etc.
* **-size \[parameter] —** Search by size. Prepend a +/- to specify greater than or lesser than. Add another size with an accompanying parameter to search within a size range. To specify sizes, append the following values.

  * **c —** bytes
  * **k —** kilobytes
  * **M —** Megabytes
  * **G —** Gigabytes
* **Ex:** 

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





