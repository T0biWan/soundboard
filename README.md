# soundboard

> A mobile first web app to play sounds.
>
> Give your pen & paper adventures more depth with or annoy your friends.

![screenshot](screenshot.png)

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

## Adding sounds

Edit `src/sounds.json` and add an array to the _topics_-object where you can add your sounds, for example:

```json
"atmosphere": [
  {"title": "thunder", "sound":"URL"}
]
```

After that you have to compile the project again:

```
npm run build
```

## Built With

* [Vue.js](https://vuejs.org/) - The web framework used
* [Bulma](https://bulma.io/) - The css framework used
* [Freesound](https://freesound.org) - The sounds

## Licensing

The code in this project is licensed under MIT license.
