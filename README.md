# AudioBookConverter

End goal:
Concatenates multiple mp3 files together and transcodes to opus for significantly reduced filesize

Note: not sure if sandisk clip jam supports opus yet so just using mp3 for now

# Concat mp3

cd into dir with .mp3 files
Works on windows:
```
ls *.mp3 | \
    sed -e "s/\(.*\)/file '\1'/" | \
    ffmpeg -protocol_whitelist 'file,pipe' -f concat -i - -c copy output.mp3
```
Works on Mac:
```
ls *.mp3 | sed -e "s/\(.*\)/file '\1'/" >list.txt
bookName=une_partie_de_badminton
ffmpeg -protocol_whitelist "file,pipe" -f concat -i ./list.txt -c copy -metadata album="$bookName" ../outputs/$bookName.mp3
```
## Change ID3 Album Tag to Title!

The Album is what shows up as the title on the Sandisk Clip Jam
