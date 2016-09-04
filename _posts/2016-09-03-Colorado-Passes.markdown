---
layout: post
title: Colorado passes traversed by unmaintained roads:
---

https://en.wikipedia.org/wiki/List_of_mountain_passes_in_Colorado

- Copy <table> element for the appropriate data. Paste to text file, saved as passes.html
- Get lines with coordinates: findstr params passes.html >passes.txt (findstr is a grep-like tool for Windows. any similar tool should do fine)
- Open Passes.txt in a text editor and use Find & Replace: .*params=(.*)_N_(.*)_E_.*title=(.*) With: \1\t\2\t\3
- Find & Replace + with space (Rollins+Pass -> Rollins Pass)
- Find & Replace (.*)\t(.*)\t(.*) with <Placemark><name>\3</name><Point><coordinates>\2,\1</coordinates></Point></Placemark>
- Add KML header and footer above and below the new <Placemark> elements

Header:
~~~
<?xml version="1.0" encoding="UTF-8"?>
<kml xmlns="http://www.opengis.net/kml/2.2">
   <Document>
~~~
Footer:
~~~
   </Document>
</kml>
~~~



- Save as KML file and upload to Google Maps.

