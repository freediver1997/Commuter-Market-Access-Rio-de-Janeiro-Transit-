# Commuter Market Access Analysis – Rio de Janeiro
# Thesis: Evaluating the Economic Impact of Rio de Janeiro’s New Transit: A Study in the Context of the 2016 Olympic Games

## Objective
This project develops a commuter market access measure to evaluate the economic impact of new public transit infrastructure in Rio de Janeiro in the context of the 2016 Olympic Games.

## Business Relevance
Market access is a key indicator for understanding how transportation infrastructure affects:
- Labor market accessibility
- Residential and more generally property prices
- Urban development

## Approach
- Integration of geospatial and transport data
- Calculation of travel times between regions
- Construction of a commuter market access index based on accessibility to jobs

## Tech Stack
- Python
- Geospatial data processing
- Ubuntu

## Project Structure
- scripts/: calculation of market access metric (partially omitted)
- data/: input datasets (partially omitted)
- outputs/: generated results for CMA 

## Notes
Please note this repository contains a focused component of a larger master’s thesis and not all its content is made available in this repository.
Large datasets are not included due to size constraints and copyright.


############### Accessing WSL OSM DATA

Step 1: Download the 2018 OSM Data
Run the following in Ubuntu (WSL) to download the Brazil OSM file from Jan 1, 2018:

wget https://download.geofabrik.de/south-america/brazil-180101.osm.pbf

Step 2: Get the Boundaries of Metropolitan Region of Rio de Janeiro
Accessed Rio’s boundary file in .poly format from OSM Boundaries API (personal key):

curl -L -o rio-metro-region.poly "https://osm-boundaries.com/api/v1/download/d0f2a704ac8371b88806fb5a5f29db3d194b82a3?apiKey=da2ac30656f1b95c56753890ee2ba181"

Step 3: Decompress the .poly file in UTF Format
mv rio-metro-region.poly rio-metro-region.poly.gz
gunzip rio-metro-region.poly.gz
file rio-metro-region.poly
(Expect output: Unicode text, UTF-8 text)


Step 4: Extract Rio de Janeiro from the full Brazil dataset
osmium extract --polygon=rio-metro-region.poly brazil-180101.osm.pbf -o rio-2018.osm.pbf