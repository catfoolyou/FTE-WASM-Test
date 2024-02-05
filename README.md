# FTE Web Bundler

All of the stuff has been compiled for your convinience, just load up the pak files from id1 for Quake and lq1 for LibreQuake to play.

The original source can be found at https://github.com/shpuld/ftewebbundler/

## Compiling from scratch

This tool is written in Javascript and runs on Node using the Express framework to keep the code minimal. You'll need both node and npm to use the tool.

First install the dependencies using npm i

This repo does not contain the actual FTE web build to free it from GPL license.You'll have to get it yourself, either from https://fte.triptohell.info/moodles/web or by building the engine yourself with emscripten if you really know what you're doing (I don't). You'll need the following files ftewebgl.html, ftewebgl.js and ftewebgl.wasm. You'll need to put them in the /fte directory.

Your game project doesn't need to be in the same directory as FTE Web Bundler as the path to it is given via arguments. Your project needs to have a .fmf file, the script expects a default.fmf in the same directory where your fteqw binary would normally reside.

Launch the script using node index.js <path-to-game-directory> in my setup it was node index.js ../ld49/game, as my project directory (ld49) was on the same level as the ftewebbundler directory. Note that you need to pass the game directory, so not just the project directory. In vanilla quake this would be id1, in my templates it's always game.

If everything went right, navigate to http://localhost:8000 in your preferred browser and it should have the FTE Web Developer frame with the game in the middle. After this any changes to progs.dat, qwprogs.dat, csprogs.dat or menu.dat will update the bundle, note that currently no other files are monitored so changing art alone won't trigger a change, you'll need to hit compile again.