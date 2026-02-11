# Pianistic Coherence vs. Performer Agency in AI-Mediated Piano Improvisation

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

Place your training data in the `Training-Data/` directory:

- `giantmidi_full_train.pickle` - training dataset (train_selection.py)
- `giantmidi_full_test.pickle` - Validation dataset (train.selection)
- `giantmidi_full_melody_train.pickle` - Monophonic training dataset (train_selection.py)
- `giantMIDI_full_melody_test.pickle` - Monophonic Validation dataset (train.selection)


### 3. Training Commands

#### Train:
Edit `train.py` to choose a model (models in `models.py`) to set the variable "model_name="
By default, model_name='no_dtime_good_reference'

Then, execute:
```bash
python train.py
```

### Checkpoints

To use the default `no_dtime_good_reference` model
1. download the checkpoint file:
https://drive.google.com/file/d/1CR90pEQwYupaEnG91ZI7Rd9iKVzbiXG8/view?usp=drive_link
2. put the file in the ./save_models folder


### Real-time Interaction

Interaction, generating buttons from MIDI keyboard or qwerty keyboard, 
starting with a context extracted from a MIDI file

```bash
python interaction_buttons.py
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

