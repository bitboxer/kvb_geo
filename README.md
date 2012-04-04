# KVB train and bus stops

This data is grabbed from openstreemap.org and is under CC BY-SA.

## Structure

The structure in the csv file is #KVB-ID#;#Name#;#Lat#;#Long#;#Type#

The KVB-ID is the internal number of the kvb system. You can use that id
to get additional data from kvb-koeln.de . One example would be 
http://www.kvb-koeln.de/german/hst/overview/885

## Missing data

Some stations don't have a coordinate. Those stations could not be
automatically matched with the openstreetmap data. I will fix those
soon.

## KML and other formats

I will add a little converter script that creates different output
formats in the next days. Stay tuned.

## Forking

Do you want to participate? Just fork and send me a pull request. I am
happy about everyone who wants to help!
