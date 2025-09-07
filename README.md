# Sound Shader Studio

An application for creating music visualizations.

## Stack

Some technologies:
* Tauri
* Rust backend for file handling, format conversions stuff, etc.
* Vue frontend
* Tailwind CSS for styling
* rete for graph node UI
* daisyUI for other random UI
* ffmpeg for video generation/conversions
* GLSL for shaders, webGPU
* Audio analysis is FFT and also beat detection

Maybe do some ML for song structure detection? Not sure if that is good idea.

Main application is creating cool videos to show off newly released music.
Some things you can do:
* Composite existing video footage under generated content
* Add warps and overlays in time to beats/music
* Sequence different sections, crossfade between sections
* Automatically add intro and outro slides
* Connect shaders and images with graph language

## Development

Setup prerequisites: https://tauri.app/start/prerequisites/

Build and run:
    npx tauri dev

On my system I sometimes have to right-click in the app and do a "reload" if the
app starts before the dev server is ready. First compile may take a bit.

