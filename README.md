# GLAM Hack '18

## Demo

For a demo see here [https://game.annotat.net](https://game.annotat.net)

## Set up your own environment

1. `git clone https://github.com/google/emoji-scavenger-hunt`
2. `cd emoji-scavenger-hunt/training/`
3. `docker build . -t model-builder`
4. Copy images to `/path/to/data/images`
4. `docker run -v /path/to/data:/data -it model-builder`
5. `cp /path/to/data/saved_model_web/* dist/model`
6. `cp /path/to/data/scavenger_class.ts src/js`
7. `yarn prep`
8. `yarn build`
