* operate on multiple file, and folders
* does not remove original file

# Compress multiple files
* `zip out.zip file1 file2`
* `-r` to make recursive work
  - `zip out.zip -r dir1` includes things inside `dir1`

# View file list in a zip file
* `unzip -l out.zip`
* `zip -sf out.zip`

# View file content in a zip file
* `unzip -c out.zip` --> all files' content
* `unzip -c out.zip dir1/file2` --> single file content (with some meta info)
* `unzip -p out.zip dir1/file2` --> preview single file content (without meta info)

# to extract
- `unzip myzip.zip`
- `unzip myzip.zip myfolder/myfile.*` specified files only
