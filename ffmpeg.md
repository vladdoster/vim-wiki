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

## convert gif to video

### function

```zsh
gif-2-mov(){
  ffmpeg -i "${1}" -c:v libx264 -crf 0 -pix_fmt yuv444p ${1:r}.mov
}
```

### all gifs

```zsh
for f in *.gif; ffmpeg -i "$f" -c:v libx264 -crf 0 -pix_fmt yuv444p ${f:r}.mov
```

Note: `:r` removes extension from file
