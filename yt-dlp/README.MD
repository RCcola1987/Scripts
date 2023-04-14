# Scripts to be used with yt-dlp
The scripts in this folder will be explained below

## Scripts

### yt-dlp-channel-dl.sh

`yt-dlp -i -N 2 --cookies cookies.txt --merge-output-format mkv -o "%(channel)s/%(title)s.%(ext)s" --windows-filenames --download-archive "channel folder name/video-ids.txt" --write-subs --sub-langs en-orig,en --convert-subs srt --add-metadata --write-comments --write-thumbnail --write-automatic-subs --write-description --embed-thumbnail --embed-metadata --embed-chapters --embed-info-json --embed-subs https://www.youtube.com/@channel-name/videos`

- -i = Ignore Errors - This is uesed since Youtube tends to error on cover images and subs. If this is omitted the script will fail at random points.
- -n 2 = Number of concurrent download threds. This only applys to downloading more than one video part at a time. @ seems to be the safest so to not get the dreded 429 too many requests error on Youtube.
- --cookies = Required for age restricted and for highest resoultion content.
- --merge-output-format mkv = This will combine the best audio and video streams into a single mkv file.
- -o "%(channel)s/%(title)s.%(ext)s" = This will automatically create the correct output folders and file nameing. **Note** you need to download one video to get the actually folder name before the video-ids.txt will work.
- --windows-filenames = Outputs files with only Windows valid characters. I have found it eliminates issues with using Linux and Windows with the outputed files.
- --download-archive "channel folder name/video-ids.txt" = Will save each video id to the file inside the channel folder. Make sure to change the folder name to the correct one for the channel you are downloading. Also this will prevent needing to re-query Youtube for files you alredy have downloaded.
- --write-subs = This will tell yt-dlp to save the subtitles for the video being downloaded.
- --sub-langs en-orig,en = This tells yt-dlp to only download the english subs. If this is omitted the script will fail very quickly due to Youtube 429 too many requests error. If you want a differint language than english then change the command to your language. EX ru.
- --convert-subs srt = Converts subs to srt file format
- --add-metadata = Adds metadata to the outputed MKV file
- --write-comments = Will save video comments into a json file
- --write-thumbnail = This will attempt to save the video thumbnail but in most cases seems to fail due to Youtubes servers.
- --write-automatic-subs = Will output the auto generated subs for a video.
- --write-description = Will save the video description into a text file with the video.
- --embed-thumbnail --embed-metadata --embed-chapters --embed-info-json --embed-subs = These embed all the info downloaded into the MKV file
