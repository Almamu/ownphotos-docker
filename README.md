# How to use
## Testing/production environments
Provided by ```docker-compose.yml```, downloads the container images directly from https://hub.docker.com and builds the required network configuration and machines.

It's as easy as running:
```
docker-compose up -d
```
After the download and creation of the containers, you can go to http://localhost:3000 and access Ownphoto's web interface. For configuration options please check each project's documentation:
- http://github.com/Almamu/ownphotos (backend)
- http://github.com/Almamu/ownphotos-frontend (frontend)

# How to use
## Developing environments
Provided by ```docker-compose.dev.yml```, requires a specific folder structure to work. First you need to clone all the ownphotos repositories needed and create the logs and pictures folders used for testing the system:
```
.
├── ownphotos
├── ownphotos-docker
├── ownphotos-frontend
├── ownphotos-proxy
├── logs
├── thumbnails
└── pictures
```
- http://github.com/Almamu/ownphotos (backend)
- http://github.com/Almamu/ownphotos-frontend (frontend)
- http://github.com/Almamu/ownphotos-docker (this repository)
- http://github.com/Almamu/ownphotos-proxy (proxy)

Once the structure is setup the easier way to get started is running
```
docker-compose -f docker-compose.dev.yml up --abort-on-container-exit
```
This will start the containers's initialization procedures and prepare all the virtual directories to be able to do changes live on the app without needing to extra setup. If any of the machines stops the whole environment will stop so you can debug the issue and fix it.

If you make any changes on the requirements for the applications you might need to rebuild one or more containers specifically to update the requirements. You can force this after the first startup:
```
docker-compose -f docker-compose.dev.yml up --build <machine-name>
```