you download a pdf and have to analyse it and open it, so i think i'll need a tool for it.
use `pdfinfo -meta file-name` and didnt get much, tried to catch a base64 looking name to ascii but it didnt work.
There are 2 parts to the flag, for the first part:
`pdftotext f2f-final.pdf` creates a text file of the same name in local directory, upon analysing you realise it looks like the end of a flag.
for the 2nd part:
do `file pdf-name` and you get the info that it contains a png image, so try converting pdf to png by doing `mv f2f-final.pdf f2f-final.png` and it becomes a png image.
now to analyse or open it from terminal, use eog. `eog f2f-final.png` you get the 1st part of the flag!
COmbine the 1st and 2nd part, and you get your flag!