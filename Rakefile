#!/usr/bin/env rake
# encoding utf8
require 'csv'
require 'json'
require 'builder'

task :default => [:json, :kml]

def csv_to_hash
  stations = {}
  CSV.foreach("kvb_stops.csv", {:col_sep => ";", :quote_char => '$'}) do |row|
    if stations[row[0]].nil?
      stations[row[0]] = {
        "kvb-id" => row[0],
        "station" => row[1],
        "points" => []
      }
    end
    stations[row[0]]["points"] << {
      "lat" => row[2],
      "long" => row[3],
      "type" => row[4]
    }
  end
  stations
end

def blank(str)
  str.nil? || str.length == 0
end

desc "Creates a JSON file"
task :json do
  puts "Generating JSON"
  File.write("kvb_stops.json", csv_to_hash.values.to_json + "\n")
end

desc "Create a KML file"
task :kml do
  puts "Generating KML"
  builder = Builder::XmlMarkup.new
  builder.instruct! :xml, :version=>"1.0", :encoding=>"UTF-8"

  xml = builder.kml("xmlns"=>"http://www.opengis.net/kml/2.2") do |kml|
    kml.Document do |doc|
      doc.name "KVB train and bus stops"

      csv_to_hash.values.each do |station|
        station["points"].each do |point|
          if (!blank(point["lat"]) && !blank(point["long"]))
            doc.Placemark do |place|
              place.name station["station"]
              place.Point do |p|
                p.coordinates "#{point["long"]},#{point["lat"]}"
              end
            end
          end
       end
      end
    end

  end

  File.write("kvb_stops.kml", xml)
end
