# ffmpeg

## remove audio from a video

```bash
ffmpeg -i "$input_file" -c copy -an "$output_file"
```

## remove audio from multiple videos via zsh

```zsh
for f in *.mp4; ffmpeg -i "$f" -c copy -an "silent-$f";
```

## download m3u8 stream

```zsh
ffmpeg -i <url.m3u8> -c copy <output.mkv>
```
