# Building [alacritty](https://github.com/alacritty/alacritty) in docker through [earthly](https://earthly.dev/)

Im a, sometimes sad, user of homebrew for linux. If some stuff needs to get compiled, im targeted with strange overwritten LD dirs by brew and a messy `$PATH`. So i thought about building alacritty through docker. I got a big fan of earthly in the last months. So why not just use this? Works just fine.

## Building

    earthly --artifact +build/alacritty .
