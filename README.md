# Find Me an Exhibit

Are you ready to take up the challenge? Film categories of objects in the exhibition "History of Switzerland" running against the clock.

The app displays one of several categories of exhibits that can be found in the exhibition (like "cloths", "paintings" or "clocks"). Your job is to find a matching exhibit as quick as possible. You don't have much time, so hurry up!

Best played on portable devices. ;-)

The frontend of the app is based on the game "[Emoji Scavenger Hunt](https://github.com/google/emoji-scavenger-hunt)", the model is built with [TensorFlow.js](https://js.tensorflow.org/) fed with a [lot of images](https://opendata.swiss/en/dataset?q=&organization=schweizerisches-nationalmuseum-snm) kindly provided by the [National Museum Zurich](https://www.nationalmuseum.ch/e/). The app is in pre-alpha stage.

## Demo

For a demo see here [https://game.annotat.net](https://game.annotat.net)

## Set up your own environment

Requirements:

* [`git`](https://git-scm.com/) (at least until we provide a first [release](https://github.com/dataramblers/glamhack18/releases))
* [`docker`](https://docker.com)
* [`yarn`](https://yarnpkg.com)

1. `git clone https://github.com/google/emoji-scavenger-hunt`
2. Go to the folder of the Dockerfile: `cd emoji-scavenger-hunt/training/`
3. Build the docker image: `docker build . -t model-builder`
4. Create a custom directory with a mandatory subfield `images`;
5. Copy images to an arbitrary subfield of the `images` directory, each
   category of images in a dedicated field (e.g. for pictures on armours: `/path/to/custom/dir/images/armours`)
6. Run the docker container to build the model: `docker run -v /path/to/custom/directory:/data -it model-builder`
7. Copy the created models to the `dist/model` folder of the git
   repository: `cp /path/to/data/saved_model_web/* dist/model`
8. Adapt the `scavanger_class.ts` in `/path/to/custom/dir` to your image
   categories (the `name` field of the objects must match to the names of your
category folders)
8. Copy the changed `scavenger_class.ts` file to `src/js`: `cp /path/to/data/scavenger_class.ts src/js`
9. Install the needed dependencies: `yarn prep`
10. Build the application `yarn build`
11. Load `dist/index.html` in your preferred webbrowser
