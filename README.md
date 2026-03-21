# Piano transcription inference

This toolbox is a piano transcription inference package that can be easily installed. Users can transcribe their favorite piano recordings to MIDI files after installation. To see how the piano transcription system is trained, please visit: https://github.com/bytedance/piano_transcription.

## Demos
Here is a demo of our piano transcription system: https://www.youtube.com/watch?v=5U-WL0QvKCg

## Installation


1. CREATE A NEW DIRECTORY "PIANO"  AND CHANGE TO THIS DIRECTORY
```bash
mkdir PIANO
cd PIANO
```

2. CREATE A NEW ENVIRONMENT "PIANO" AND ACTIVATE IT
```bash
conda create --name PIANO python=3.11
conda activate PIANO
```
3. DOWNLOAD PACKAGES
```bash
pip install librosa==0.10.2
pip install numpy==2.0.2
pip install audioread==3.0.1
pip install mido==1.3.3
pip install matplotlib==3.10.0
pip install torchlibrosa==0.1.0
pip install ipywidgets==8.1.5
pip install librosa==0.10.2
pip install torch==2.6.0
pip install pretty_midi
pip install fluidsynth
pip install ipykernel
pip install jupyter
pip install notebook
python -m ipykernel install --user --name PIANO --display-name "Python 3.11.11 (PIANO)"
```

4. DOWNLOAD THE PIANO_TRANSCRIPTION_INFERENCE LIBRARY AND UNCOMPRESS IT TO YOUR "PIANO" DIRECTORY
Go to:
https://github.com/mirekyahoo/piano_transcription_inference
Press the green "CODE" button and download the zip file


3. DOWNLOAD PIANO SAMPLES
Download Yamaha S6 soundfonts from:
https://drive.google.com/file/d/1IyAYg882PNWYwDHzgorQWWLx1PaogZhW/view

... and move this file to your PIANO/PIANO_TRANSCRITION_INFERENCE/SOUNDFONTS directory

4 DOWNLOAD FLUIDSYNTH FILES (WINDOWS VERSION) FROM:
https://github.com/FluidSynth/fluidsynth/releases/tag/v2.4.3

5. START JUPYTER NOTEBOOK from PIANO/PIANO_TRANSCRITION_INFERENCE directory

```bash
jupyter notebook
```


## Usage
Want to try it out but don't want to install anything? We have set up a [Google Colab](https://colab.research.google.com/github/qiuqiangkong/piano_transcription_inference/blob/master/resources/inference.ipynb).

```python
python3 example.py --audio_path='resources/cut_liszt.mp3' --output_midi_path='cut_liszt.mid' --cuda
```

This will download the pretrained model from https://zenodo.org/record/4034264. 

Users could also execute the inference code line by line:

```python
import librosa
from piano_transcription_inference import PianoTranscription, sample_rate

# Load audio
audio, _ = librosa.load(path=audio_path, sr=sample_rate, mono=True)

# Transcriptor
transcriptor = PianoTranscription(device='cuda', checkpoint_path=None)  # device: 'cuda' | 'cpu'

# Transcribe and write out to MIDI file
transcribed_dict = transcriptor.transcribe(audio, 'cut_liszt.mid')
```

## Visualization of piano transcription

**Demo.** Lang Lang: Franz Liszt - Love Dream (Liebestraum) [[audio]](resources/cut_liszt.mp3) [[transcribed_midi]](resources/cut_liszt.mid)

<img src="resources/cut_liszt.png">

## FAQs
This repo support Linux and Mac. Windows has not been tested.

If users met "audio.exceptions.NoBackendError", then check if ffmpeg is installed.

If users met the problem of "Killed". This is caused by there are not sufficient memory.

## Applications

We have built a large-scale classical piano MIDI dataset https://github.com/bytedance/GiantMIDI-Piano using our piano transcription system.

## Cite
[1] High-resolution Piano Transcription with Pedals by Regressing Onsets and Offsets Times, [To appear], 2020
