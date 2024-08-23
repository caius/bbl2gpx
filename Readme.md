# Blue Boat Log to .gpx

BBL has a .gpx export feature, but ends up with just a list of waypoints containing lat/long, but no timestamp.

This will generate a GPX from the voyage more akin to Navionics GPX export, with a track containing waypoints and timestamps.

## Instructions to export whole profile

Login at https://blueboatlog.com/ and from the network tab grab the Authorization header value ("Bearer …") - we'll use this to authenticate to the API for feeds.

Grab your feed of events into a temporary file

```shell
curl --header "Authorisation: Bearer …" "https://api.blueboatlog.com/v3/trip?limit=25&skip=0&sort=enddate&type=mineall" > tmp/feed.json
```

Then we can run the script against the feed to get things exported:

```shell
./bin/bbl-feed-to-gpx < tmp/feed.json
```

If you have the feed id for a single track to export, you can do that with the other script:

```shell
./bin/bbl-to-gpx ID
```

All exported gpx will end up in the `exports` directory.

## Notes

<http://www.topografix.com/GPX/1/1/>
