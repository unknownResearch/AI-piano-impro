# Real-Time Conditioning Strategies for Shared Agency in AI-Mediated Piano Improvisation

## Requirements

Python 3.9.19

### Dependencies

```bash
torch
tqdm 
datasets
einops
wandb
matplotlib
python-rtmidi
pyfluidsynth
scipy
pretty_midi
```

Install with:
```bash
pip install torch tqdm datasets einops wandb matplotlib python-rtmidi pyfluidsynth
```

## Project Structure

```
AI-mediated-pianistic-improvisation/
├── train.py               # Standard training script
├── params.py              # Default parameters
├── models.py              # Model configurations
├── x_transformer.py       # Transformer implementation
├── model_loader.py        # Model loading utilities
├── interaction_arrows.py  # real-time interaction with arrows
├── interaction_buttons.py # real-time interaction with buttons
├── interaction_1_button.py# real-time interaction with 1 button
├── midi_processors.py     # MIDI processing functions
├── visualizer.py          # Real-time visualization
├── Training-Data/         # Training datasets
├── save_models/           # Saved model checkpoints
└── samples/               # Sample MIDI files
```

## Training

### 1. Dataset Preparation

1. download the dataset files:
https://drive.google.com/drive/folders/17_JasXY5BtLA7QcIJl10rg-B4Q9bKJuZ?usp=sharing

Place your training data in the `Training-Data/` directory:

- `giantmidi_full_train.pickle` - training dataset (train_selection.py)
- `giantmidi_full_test.pickle` - Validation dataset (train.selection)
- `giantmidi_full_melody_train.pickle` - Monophonic training dataset (train_selection.py)
- `giantMIDI_full_melody_test.pickle` - Monophonic Validation dataset (train.selection)


### 3. Training Commands

#### Train:
Edit `train.py` to choose a model (models in `models.py`) to set the variable "model_name="
By default, model_name='no_dtime_good_reference' (12 buttons) or model_name='melody_arrow_v10' (7 arrows) 


Then, execute: 
```bash
python train.py
```

### Checkpoints

1. download the checkpoint files:
https://drive.google.com/drive/folders/17_JasXY5BtLA7QcIJl10rg-B4Q9bKJuZ?usp=sharing
2. put the file in the ./save_models folder


### Real-time Interaction

Interaction, generating buttons from MIDI keyboard or qwerty keyboard, 
starting with a context extracted from a MIDI file

```bash
python interaction_12buttons.py
```
or
```bash
interaction_5buttons.py
interaction_1_button.py
interaction_88_buttons.py
interaction_arrows.py
```

### 2. Model loaders

Use `no_dtime_good_reference` model by default

Available model types:
- `autoencoder` - Standard encoder-decoder
- `autoencoder_no_dtime` - Without delta-time tokens
- `autoencoder_w_encoder_antic` - With dtime in the encoder
- `decoder_only` - Decoder-only model (decorder tester)
- `encoder_only` - Encoder-only model (button-compression tester)

## Visualization

Real-time visualization is available during interactive modes:
- Note activity display
- Button state visualization  
- Melodic contour representation

