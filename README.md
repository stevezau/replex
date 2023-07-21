# Replex (WIP)

![plot](./example.png)

Plex proxy with the following features:

- Merge movies and shows from hubs on home.
- Remove watched items from hubs in home and library recommended

Make sure you have collections/recommended rows with the same name in both movies and shows (aka trending) as it will be merged by name.

### Usage example

Run the docker image

```
docker run --rm -it -p 80:80 -e REPLEX_HOST="http://10.0.0.3:42405" ghcr.io/sarendsen/replex-nginx:latest
```

add your proxy url to plex "Custom server access URLs" (ex http://0.0.0.0:80)

then access your proxy url http://0.0.0.0:80

fyi: this isnt a fully fledged proxy and doesnt aim to be. I suggest putting it behind a proper (reverse) proxy and only route the following paths (and it subpaths) to this app. And docker image including nginx exists at ghcr.io/sarendsen/replex-nginx and a version without nginx at ghcr.io/sarendsen/replex

- /hubs
- /replex

### Settings
Settings are set via [environment variables](https://kinsta.com/knowledgebase/what-is-an-environment-variable/) 

| Setting        	       | Default 	| Description                                                            	|
|--------------------------|------------|---------------------------------------------------------------------------|
| REPLEX_HOST              | -      	| Plex host we want to proxy                                             	|
| REPLEX_INCLUDE_WATCHED   | false    	| If set to true, remove watched items from hubs.                        	|
