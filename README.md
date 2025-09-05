# How to use Whisper to transcribe a YouTube video - Tutorial
In this tutorial you will learn how to use OpenAIs Whisper to transcribe a YouTube video

[ [Full written guide](https://lablab.ai/t/whisper-transcribe-youtube-video) ]

## What is Whisper?

Whisper is an automatic State-of-the-Art speech recognition system from OpenAI that has been trained on 
680,000 hours 
of multilingual and multitask supervised data collected from the web. This large and diverse 
dataset leads to improved robustness to accents, background noise and technical language. In 
addition, it enables transcription in multiple languages, as well as translation from those 
languages into English. Unlike DALLE-2 and GPT-3, Whisper is a free and open-source model. OpenAI released
 the models and code to serve as a foundation for building useful
applications that leverage speech recognition.

# How to transcribe a YouTube video

In this tutorial we will use Whisper to transcribe a YouTube video. We will use the Python package "Pytube" to 
download convert the sounds into a `MP4` file. You can find the repo of Pytube [here](https://github.com/pytube/pytube)

## Installing prerequisites

First, we need to install the Pytube Library. You can do this by running the following command in your terminal:

```bash
!pip install -- upgrade pytube
```

Since pytube is outdated, you also need to install pytubefix (which is maintained and working as of September 2025):
```bash
!pip install pytubefix
```

And finally, we'll install whisper for the actual conversion to text:
```bash
!pip install git+https://github.com/openai/whisper.git -q
```

## Downloading the audio

For this tutorial i'll be using [this](https://www.youtube.com/watch?v=x7X9w_GIm1s) "Python in 100 Seconds" Video. 

Create a python file. We will provide the link to the video and use pytubefix to convert its audio to `MP4`:

```python
from pytubefix import YouTube
from pytubefix.cli import on_progress

# Reading the above Taken movie Youtube link
url = "https://www.youtube.com/watch?v=x7X9w_GIm1s"

yt = YouTube(url, on_progress_callback=on_progress)
print(yt.title)

ys = yt.streams.get_highest_resolution()
ys.download()
```

The output is a file named like the video title in your current directory. In our case, the file is named `Python in 100 Seconds.mp4`

## Audio to text

The next step is to convert audio into text. We can do this in three lines of code using whisper:

* import whisper
* load the model
* transcribe the audio file

We'll use the "base" model for this tutorial. You can find more information about the 
models [here](https://github.com/openai/whisper/blob/main/model-card.md). Each one of them has tradeoffs between 
accuracy and speed (compute needed).

```python
import whisper

model = whisper.load_model("base")
text = model1.transcribe("Python in 100 Seconds.mp4")

#printing the transcribe
text['text']
```

You can find the full code as Jupyter Notebook [here](https://github.com/lablab-ai/How-to-use-OpenAIs-Whisper-Tutorial/blob/main/whisper-tutorial.ipynb)

**Thank you** for reading. If you enjoyed this tutorial you can find more and continue reading 
[on our tutorial page](https://lablab.ai/t/) - [Fabian Stehle](https://github.com/ezzcodeezzlife), 
Junior Data Scientist at [New Native](https://newnative.ai/)

---

[![Artificial Intelligence Hackathons, tutorials and Boilerplates](https://storage.googleapis.com/lablab-static-eu/images/github/lablab-banner.jpg)](https://lablab.ai)

## Join the LabLab Discord

![Discord Banner 1](https://discordapp.com/api/guilds/877056448956346408/widget.png?style=banner1)  
On lablab discord, we discuss this repo and many other topics related to artificial intelligence! Checkout upcoming [Artificial Intelligence Hackathons](https://lablab.ai) Event


[![Acclerating innovation through acceleration](https://storage.googleapis.com/lablab-static-eu/images/github/nn-group-loggos.jpg)](https://newnative.ai)

