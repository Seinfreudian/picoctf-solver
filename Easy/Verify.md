You get a folder full of files, you have a hash. Now compare the hash of each file with the specific file to check if it's the correct file.
`sha256sum <file-name>` gives the hash of a specific file
`sha256sum <folder-name>/*` gives hash of all files in the folder
to match hashes use a grep command:
`sha256sum <folder-name>/* | grep -i "$<hash-value>`
gives us the file name
then decrypt the file using `./decrypt.sh files/c6c8b911`
YOu get your flag!