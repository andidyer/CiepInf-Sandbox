# CiepInf Sandbox

This is a repository to allow annotators on the CiepInf project to practice annotating files using Brat locally, on their own localhost, before working on the live version.

This repository has the makings of a [Docker](https://www.docker.com/) image and container to run the Brat webserver locally. This means that you do not have to install Brat locally. However, you do need to have Docker installed on your desktop.

## BRAT Docker

Based on [this repository](https://github.com/ddevaraj/docker-brat) and [this repository](https://github.com/cassj/brat-docker).

```
docker build -t ciepinf-sandbox .
docker run --name brat-server -p 8080:80 -v "$(pwd)/shared:/usr/local/apache2/htdocs/brat/data/shared" -d ciepinf-sandbox
```

The web interface is available at `http://127.0.0.1:8080/brat/`.

You can use `docker-machine ip default` to check your IP, which is required on Windows with Docker Toolbox.


## Getting Started

Using the above launch command, the `shared/` folder is shared with the container and will be available as a subfolder in BRAT's workspace.

`shared/Infstat/CiepInf/SandboxFiles` is where the annotation data is located. You will see folders for each language (currently only English). Select any of the files to start annotating.

## Manually adding/modifying files

You can add new folders and files for annotation within this directory, and they will appear for annotation in Brat when you next load it.

Files for annotation must be in txt format, and must have an equivalent `.ann` file, which should be empty at initialisation.

For example, you could add the following structure under `shared/Infstat/CiepInf/SandboxFiles`:

```
MyLanguage
-MyBook1
--MyBook1_mylanguage1.txt
--MyBook1_mylanguage1.ann
--MyBook1_mylanguage2.txt
--MyBook1_mylanguage2.ann
```
