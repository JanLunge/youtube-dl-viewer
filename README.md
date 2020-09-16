# youtube-dl-viewer

![screenshot](https://github.com/wlard/youtube-dl-viewer/blob/master/screenshots/01.png?raw=true)

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).



# create needed dirs
```
mkdir -p /content/downloads
mkdir -p /content/videos
mkdir -p /static/v
```
# add a video
this downloads a video to the downloads folder inside content and then moves the json into the content folder for videos and the video file into the static serving folder
```
youtube-dl https://www.youtube.com/watch?v=y7AKKqb8Wrs --format mp4 --write-info-json --write-thumbnail -o 'content/downloads/f%(format_id)s.%(ext)s' && mv content/downloads/*.json content/videos/ && mv content/downloads/* static/v/
```

# generate static pages
`yarn generate`
then put the dist folder into your webserver 
for testing i use spark https://github.com/rif/spark
```
cd dist
~/go/bin/spark -port="3001"
```