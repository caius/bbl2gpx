# Blue Boat Log to .gpx

BBL has a .gpx export feature, but ends up with just a list of waypoints containing lat/long, but no timestamp.

This will generate a GPX from the voyage more akin to Navionics GPX export, with a track containing waypoints and timestamps.

## Instructions to export a single trip

Find the trip on the website and grab the id from the end of the URL, pass to the script as sole argument:

```shell
./bin/bbl-to-gpx ID
```

## Instructions to export a whole profile of trips

Find the profile of the user you want to export (if it's your profile, click "View My Public Profile" at the bottom of <https://blueboatlog.com/profile>). eg, <https://blueboatlog.com/user/616c7b54623ced5c16537e9c>

Then we can run the script against the profile to export the data we want:

```shell
./bin/bbl-feed-to-gpx "https://blueboatlog.com/user/616c7b54623ced5c16537e9c"
```

All exported gpx will end up in the `exports/*.gpx` directory.

The JSON data retrieved is stored in `exports/tmp/*.json` for debugging purposes, and so repeated runs don't re-fetch the same data.
