# Extracting Audio and Transcripts (https://www.youtube.com/watch?v=MPV7JXTWPWI)

## Media Processing with FFmpeg

**FFmpeg** is a powerful command-line tool used to process video, audio, and image files. It is widely used in data science, media processing pipelines, and machine learning workflows.

Typical use cases include:

* Extracting audio or frames from videos
* Converting media formats
* Preparing datasets for machine learning
* Creating clips or visualizations
* Processing large media datasets

---

# Installing FFmpeg

Download from the official site:

[https://ffmpeg.org/download.html](https://ffmpeg.org/download.html)

### Recommended Version

If unsure which build to download, choose the **static build**.
It contains everything needed in a single executable.

### Windows Installation Steps

1. Download the **static build zip**.
2. Extract the archive.
3. Open the `bin` folder.
4. Copy `ffmpeg.exe`.
5. Place it in a known location (or add it to your **PATH**).

To verify installation:

```bash
ffmpeg -version
```

---

# Basic FFmpeg Commands

## Convert Video Format

```bash
ffmpeg -i input.mp4 output.avi
```

FFmpeg automatically determines the conversion based on the **output extension**.

---

## Extract Audio from Video

```bash
ffmpeg -i input.mp4 -vn output.mp3
```

`-vn` disables video and outputs only audio.

---

## Convert Without Re-Encoding

```bash
ffmpeg -i input.mkv -c copy output.mp4
```

Useful for fast container conversion.

---

## High Quality Encoding

```bash
ffmpeg -i input.mp4 -preset slower -crf 18 output.mp4
```

Lower CRF = higher quality.

Typical CRF values:

| CRF | Quality           |
| --- | ----------------- |
| 18  | visually lossless |
| 23  | default           |
| 28+ | lower quality     |

---

# Common Data Science Tasks

## Extract Frames for Computer Vision

Extract 1 frame per second:

```bash
ffmpeg -i input.mp4 -vf "fps=1" frames_%04d.png
```

Extract only the first frame:

```bash
ffmpeg -i input.mp4 -vf "select=eq(n\,0)" -vframes 1 first_frame.jpg
```

---

## Create Video from Image Sequence

```bash
ffmpeg -r 15 -i img%03d.png -c:v libx264 -vf fps=25 output.mp4
```

---

## Extract Audio for Speech Recognition

```bash
ffmpeg -i input.mp4 -ar 16000 -ac 1 audio.wav
```

Explanation:

| Option      | Meaning                                     |
| ----------- | ------------------------------------------- |
| `-ar 16000` | sample rate (recommended for speech models) |
| `-ac 1`     | mono channel                                |

---

## Trim a Video Clip

```bash
ffmpeg -ss 00:01:00 -i input.mp4 -t 00:00:30 -c copy clip.mp4
```

Extracts **30 seconds starting at 1 minute**.

---

# Useful FFmpeg Filters

## Change Audio Volume

```bash
ffmpeg -i input.mp4 -filter:a "volume=2" output.mp4
```

Volume values:

| Value | Effect        |
| ----- | ------------- |
| 2     | double volume |
| 0.5   | half volume   |

---

## Crop Video

```bash
ffmpeg -i input.mp4 -filter:v "crop=640:360" output.mp4
```

Parameters:

```
crop=width:height:x:y
```

---

## Resize Video

```bash
ffmpeg -i input.mp4 -vf "scale=1280:720" output.mp4
```

Maintain aspect ratio:

```bash
scale=1280:-1
```

---

## Rotate Video

```bash
ffmpeg -i input.mp4 -vf "rotate=45*PI/180" output.mp4
```

Rotation angles must be in **radians**.

---

# Processing Multiple Files

## Batch Audio Extraction

```bash
for f in *.mp4; do
  ffmpeg -i "$f" -vn "audio/${f%.mp4}.wav"
done
```

---

## Concatenate Videos

Create a file list:

```bash
echo "file 'input1.mp4'" > files.txt
echo "file 'input2.mp4'" >> files.txt
```

Then run:

```bash
ffmpeg -f concat -i files.txt -c copy output.mp4
```

---

# Download Audio with yt-dlp

`yt-dlp` is a powerful tool for downloading media from video platforms.

Install:

```bash
pip install yt-dlp
```

Download best audio:

```bash
yt-dlp -f "bestaudio" \
--extract-audio \
--audio-format mp3 \
--audio-quality 32k \
URL
```

Download subtitles:

```bash
yt-dlp --write-auto-subs --sub-format srt URL
```

---

# Python Integration Example

```python
import yt_dlp

def download_audio(url):
    ydl_opts = {
        "format": "bestaudio",
        "postprocessors": [{
            "key": "FFmpegExtractAudio",
            "preferredcodec": "mp3",
            "preferredquality": "192",
        }],
    }

    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        ydl.download([url])

download_audio("VIDEO_URL")
```

---

# Whisper Transcription

**Whisper** is an automatic speech recognition (ASR) model developed by OpenAI.

Install faster Whisper:

```bash
pip install faster-whisper
```

Run transcription:

```bash
faster-whisper video.mp4 --model medium --language en
```

Recommended command:

```bash
faster-whisper video.mp4 \
--print_progress \
--output_dir source \
--batch_recursive \
--check_files \
--standard \
--output_format json srt \
--model medium \
--language en
```

---

# Gemini Transcription

Google **Gemini models** support large context windows and can transcribe long audio files.

Steps:

1. Get an API key from **Google AI Studio**
2. Set environment variable

```
export GEMINI_API_KEY=your_key
```

3. Send audio for transcription.

Example request:

```bash
curl -X POST https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent \
-H "x-goog-api-key: $GEMINI_API_KEY" \
-H "Content-Type: application/json" \
-d '{
 "contents":[
   {
     "role":"user",
     "parts":[
       {"text":"Transcribe this"},
       {
         "inline_data":{
           "mime_type":"audio/mp3",
           "data":"BASE64_AUDIO"
         }
       }
     ]
   }
 ]
}'
```
