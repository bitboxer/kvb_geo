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

## Other formats for the data

The csv file is the main data file. All other files are generated from
that file. You can regenerate the other files using rake. If you need
other formats or want to enhance the current converters, feel free to
fork this project and send me a pull request!

## Forking

Do you want to participate? Just fork and send me a pull request. I am
happy about everyone who wants to help!
