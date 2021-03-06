# pybble


## Python (almost) on Pebble

It's a hack; it works. Here's a barely-even-barebones proof of concept.

## Huh?

I stumbled into this recently, and was quite surprised to realize that
the long-time wish to write apps for Pebble watch in Python was
already feasible if we jump through a few technical hoops.

Here is some code that currently only demonstrates what is possible.
I'm also structuring the glue code as a library for easy reuse.

Pybble could evolve into a Python wrapper around Pebble.js that
lets us write full Pebble apps that run on phone as compiled Javascript,
and display on the Pebble watch - giving us a powerful environment to
program our favourite smartwatch.

There are a few components to this hack:


### A Pebble Watch or Emulator

  - Watch: https://www.pebble.com/
  - Emulator:  https://cloudpebble.net


### Pebble.js

  https://github.com/pebble/pebblejs

Pebble.js lets you write Javascript apps that run on your Phone and
display on your Pebble, giving us freedom to experiment with
pure Python or Javascript libraries.


### Transcrypt

  http://transcrypt.org/

Transcrypt takes your Python code and 'transpiles' it into Javascript
code that is optimized to run inside a Javascript execution engine,
which is what we get when we run a Pebble.js script.

Since it is compiled to JS and does not have a Python runtime like
Brython gives, we have limited access to Python standard library.
However, by substituting them with native Javascript libraries and
writing a little bit of glue code, you can close your eyes and
pretend we're still in Python world. These tradeoffs are what allow
diverse use cases.


### Pybble

  https://github.com/hiway/pybble/

Pybble is an experiment to see if Pebble.js can be used with the help
of Transcrypt to make more than hello world apps.


## What works?

So far:
 - Can create Cards
 - Can hook to button clicks
 - Ajax requests work as expected
 - Websockets work as expected

## What doesn't work?

 - Websockets to LAN won't work on CloudPebble's emulator ;)

## Installation

    git clone https://github.com/hiway/pybble.git
    cd pybble
    pip install --editable . # Don't miss that last dot


## Usage

  - Edit app.py in your preferred editor
  - In terminal, run `pybble build app.py --copy`
  - Head over to https://cloudpebble.net/, create a new Pebble.JS project
  - Replace contents of app.js on cloudpebble with the minified,
    auto-generated javascript code from your computer - which was
    automatically copied to your clipboard by the previous command.
  - Tap 'Run'
