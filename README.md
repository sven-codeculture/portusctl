portusctl minimal image
===

This image contains a portus [https://github.com/openSUSE/portusctl] build in alpine and copied to a scretch image to reduce the sice as much as possible.

## Usage example

> docker run -it --rm -e PORTUSCTL_API_SERVER="your-server" -e PORTUSCTL_API_TOKEN="your-token" -e PORTUSCTL_API_USER="your-user" svenbcc/portusctl get repositories

## Flavors

- latest -> contains only the cli
- bash -> if you want to run some bash inside - contains /bin/bash + jq binaries and is based on alpine
