Generates a static website for photographers
---
# General concept
TODO creates a gallery website from photo directories. Each directory must contain some pictures as well as a `gallery descriptor`.

# config.json
This file contains all the settings necessary to build the websites with various galleries and all kind of relevant informations. Here is the description of all fields:

```javascript
{
  // Global informations about the website
  "website": {
    "name": "Film gallery",
    "author": "Jonathan Lurie",
    "authorDescription": "Just a guy with a camera",
    "description": "Some scanned analog films"
  },

  // Social media URLs, leave blank to disable the links
  "social": {
    "twitter": "http://twitter.com/jonathanlurie",
    "instagram": "https://instagram.com/jonathanlurie",
    "facebook": "https://facebook.com/jonathanluriephoto"
  },

  // Negative will create resampled images in both full size and thumb
  "photoSettings": {
    "largestSide": 1000,
    "largestSideThumb": 300
  },

  // Negative uses a work directory where your full size image are stored as well gallery descriptors
  "buildSettings": {
    "dataDir": "./data/",
    "indexingFilename": "dataIndex.json",
    "outDir": "./out/",
    // if true, will rebuild all the galleries, recreate resampled images and thumbs, even for the galleries that are already built.
    "forceRebuildAllDefault": false
  },

  // this fields are the one to fetch from each gallery descriptors. These fields will feed the graphic theme
  "fields": [
    "name",
    "description",
    "date",
    "author",

  ],

}

```


# Gallery descriptor
A gallery descriptor is a *json* file that must be present in **every** gallery folder `buildSettings.dataDir` (see the file `config.json`). The descriptor can contain several fields, but only one is mandatory: `date`. This allows Negative to order the galleries (newest on top). Here are the possible fields:

```javascript
{
  "date": "2017-02-25T01:05:35.375Z", // mandatory
  "name": "My gallery", // optional
  "author": "John Doe", //optional, overrides from config.js
  "description": "My holidays in Patagonia" // optional
}
```

If the graphic theme is built accordingly, more fields can be added and displayed.
