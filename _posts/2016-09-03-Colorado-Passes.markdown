---
layout: post
title: "Colorado passes traversed by unmaintained roads"
date:   2016-09-03 23:00:00 -0600
categories: regex location
---

[Source data](https://en.wikipedia.org/wiki/List_of_mountain_passes_in_Colorado)

[Resulting map](https://www.google.com/maps/@39.2990313,-107.46128,8z/data=!3m1!4b1!4m2!6m1!1s1zMdgiAUheo0TMRXV9D_gS9-QZOw)

- Copy <table> element for the appropriate data. Paste to text file, saved as passes.html
- Get lines with coordinates: findstr params passes.html >passes.txt (findstr is a grep-like tool for Windows. any similar tool should do fine)
- Open Passes.txt in a text editor and use Find & Replace: .*params=(.*)_N_(.*)_E_.*title=(.*) With: \1\t\2\t\3
- Find & Replace + with space (Rollins+Pass -> Rollins Pass)
- Find & Replace (.*)\t(.*)\t(.*) with <Placemark><name>\3</name><Point><coordinates>\2,\1</coordinates></Point></Placemark>
- Add KML header and footer above and below the new <Placemark> elements

Header:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<kml xmlns="http://www.opengis.net/kml/2.2">
   <Document>
```

Footer:

```xml
   </Document>
</kml>
```


- Save as KML file and upload to Google Maps.

<iframe src="https://www.google.com/maps/d/u/0/embed?mid=1zMdgiAUheo0TMRXV9D_gS9-QZOw" width="640" height="480"></iframe>

