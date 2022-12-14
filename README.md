# Video to MP3

Extract full audio from videos or use timestamps to get only a part of the full audio.


## Getting Started

### Dependencies

* Latest version of [Python](https://www.python.org/downloads/) (This project was built with Python 3.11.0).

* [Moviepy](https://pypi.org/project/moviepy/) Library, which is used to manipulate videos/audios.

### Installing

```
git clone https://github.com/riad-azz/video_to_mp3.git
```

```
cd video_to_mp3
```

```
pip install -r requirements.txt
```

### Executing program from the command line

* Extract the full audio
```python
python run.py --path='(FILEDIR)/video.mp4' --save-path='./' --filename='audio.mp3'
```
_this will save the full audio in the same folder as audio.mp3_

_save-path and filename arguments are optional (Do not include the file name in the save-path argument)_

* Extract a part of the audio
```python
python run.py --path='(FILEDIR)/video.mp4' --save-path='./' --filename='audio.mp3' --start=0 --end=11
```
_this will save the audio (from second 0 to second 11) in the same folder as audio.mp3_

_Note : Make sure start timestamp is less than the end timestamp if you include both_

* You can also include only one argument (--start or --end)
```python
python run.py --path='(FILEDIR)/video.mp4' --save-path='./' --filename='audio.mp3' --start=4
```
_this will save the audio (from second 4 to the end of the video duration) in the same folder as audio.mp3_

### Executing program from another script

You can simply copy the video_to_mp3.py to your project folder and import the function

* Example
```python
from video_to_mp3 import extract_audio

filepath = './video.mp4' # Must include video file name in this case
savepath = './audio.mp3' # Must include the name you want for the mp3 file in this case
full_audio = False # Optional, the default is set to True
# You can have one side as None in the timestamps which will mean
# that the script will finish to the end or from the start
# if you put (None, 10) the script will cut the audio from the start to the second 10
# if both are (None, None) you will just get the full audio
timestamps = (0, 11) # Required only if full_audio is set to False

extract_audio(filepath=filepath,
              savepath=savepath,
              full_audio=full_audio,
              timestamps=timestamps) 
```
