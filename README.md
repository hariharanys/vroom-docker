
# OSRM MAP CONFIGURATION

VROOM is an excellent open-source optimization engine that can provide good solutions to various real-life vehicle routing problems.


First of all let’s start by downloading a region map in OpenStreeMap. http://download.geofabrik.de

Choose your sub region:





## Screenshots
![App Screenshot](https://i.ibb.co/N6pt2gD/Screenshot-114.png)

Each region has a sub region selected according to your need.

![App Screenshot](https://i.ibb.co/6XnvSHK/Screenshot-113.png)

Open powershell and set directory to the downloaded file.

![App Screenshot](https://i.ibb.co/Hq829J9/Screenshot-115.png)

After that, run the following commands: 
docker run -t -v "${PWD}:/data" osrm/osrm-backend osrm-extract -p /opt/car.lua /data/southern-zone-latest.osm.pbf

![App Screenshot](https://i.ibb.co/GdrGy4M/Screenshot-116.png)

docker run -t -v "${PWD}:/data" osrm/osrm-backend osrm-partition /data/southern-zone-latest.osrm

![App Screenshot](https://i.ibb.co/PGHQn52/Screenshot-117.png)

docker run -t -v "${PWD}:/data" osrm/osrm-backend osrm-customize /data/southern-zone-latest.osrm

![App Screenshot](https://i.ibb.co/MB1kq8y/Screenshot-118.png)

After creating these files, we had to clone the vroom-docker.

Now you need to change the left part in osrm volumes to the path you have created your osrm data. Leave the right part as it is(/data) in docker-compose.yml file.

Also change the zone name in command: field

After this, you can start your vroom instance with docker-compose up -d

select all the osrm map and paste in separate folder named as osrm.

