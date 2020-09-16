# youtube-dl-viewer

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).



youtube-dl https://www.youtube.com/watch?v=NhVRB5sHteQ --write-info-json --write-thumbnail -o 'f%(format_id)s.%(ext)s'
mv content/downloads/*.json content/videos/
mv content/downloads/* static/v/