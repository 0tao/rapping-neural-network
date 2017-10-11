# Rapping-neural-network
I made this for my high school's programming club - which ~I'm the president/founder of~ I was the president/founder of until I graduated the other month.

It's a neural network that has been trained on rap songs, and can use any lyrics you feed it and write a new song (it now writes *word by word* as opposed to *line by line*) that rhymes and has a flow (to an extent).

# Let's hear something it made
Okay... Here's a song it wrote *word by word* using kanye's discography - excuse the vulgarities, the neural network wrote it and not me.
https://soundcloud.com/rapping_neural_network/networks-with-attitude

Here are the lyrics;
http://pastebin.com/MUDc9Unt



## Setup

Install (with python 2.x)

    pip install -U -r requirements.txt 

## Usage

### Data preperation
**If you'd like to use Kanye's lyrics - skip this section**
`Lyrics.txt` comes with Kanye's entire discography in it. You can either use this, or fill it with other lyrics.

* Avoid putting things like "[bridge]" or "[intro]" in `lyrics.txt` 

* Seperate each line by a newline

* Avoid non alphanumeric characters (besides basic punctuation)

* You don't have to retype everything - just copy and paste from some lyrics website

### Training
**Skip this part if you are using the default kanye lines**

* In `model.py`, change `artist` to the name of the new artist you've used in `lyrics.txt`

* In `model.py`, change the variable `train_mode` to `True`

* Run the program with `python model.py`, and allow training to finish.

### Generating raps

* In `model.py`, if you've trained a new network, the variable `train_mode` will be `True`, set this back to `False`

* Run the program with `python model.py`

* The rap will be written to the output of your terminal, and also to a file called `neural_rap.txt`

### Performing raps

* speech.py will "rap" the generated songs with a text to speech over a generic rap beat (`beat.mp3`), just run `python speech.py`

## How it works

Alright, so basically a markov chain will look at the lyrics you entered and generate new lines. Then, it feeds this to a recurrent neural net that will generate a sequence of tuples in the format of 

    (desired rhyme, desired count of syllables)

The program will then sift through the lines the markov chain generated, and match the lines to their corresponding tuples. The result is the rap.
