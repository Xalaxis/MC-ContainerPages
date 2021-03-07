# Docker containers for Feed The Beast (FTB) ModPacks

These containers are all created based on my https://github.com/Xalaxis/CreeperHostPackInstaller image.

This page, and all the containers are work-in-progress and subject to change, but they're stable enough for public use and they're what I use myself personally. I'm happy to add new containers and options if anyone wants.

Any issues can be reported via adding an issue at https://github.com/Xalaxis/Xalaxis-FTB-Containers/issues

## Tags

The :latest tag automatically updates to the latest version available of each Modpack once daily. Even if no new version is available, the image is rebuilt to ensure underlying container updates are propagated.

It is a long term goal that :version tags will be made that track only specific versions of the packs.

## Full Pack listing

| ModPack  | DockerHub Container | Status |
|----------|:-------------------:| ------- |
| FTB Revelation | wolfrazu/ftb-revelation | [![Build and Push Latest Versions](https://github.com/Xalaxis/FTB-Revelation/actions/workflows/build.yml/badge.svg?branch=main)](https://github.com/Xalaxis/FTB-Revelation/actions/workflows/build.yml)
| FTB Presents Direwolf 20 1.16 | wolfrazu/ftb-presents-direwolf20-116 | [![Build and Push Latest Versions](https://github.com/Xalaxis/FTB-Presents-Direwolf-20-1.16/actions/workflows/build.yml/badge.svg)](https://github.com/Xalaxis/FTB-Presents-Direwolf-20-1.16/actions/workflows/build.yml)

# Configuration

Configuration for the settings of the servers is done like a regular server, by modifying the configuration files on disk after the first launch.

The containers themselves have the following options:

## Environment variables

Variable | Purpose | Default
---------|---------|---------
MAXMEMORY | Maximum memory for the Java VM | 4G
MINMEMORY | Minimum memory for the Java VM | 3072M

## Mount locations

Container Path | Purpose
---------------|---------
/opt/minecraftftb | Location of the server files, configuration occurs in this location.
/mixins | Mix-in mods, see below.

## Mix-ins

Any content placed in the /mixins directory will be automatically added to the /mods directory of the server after the installation is complete. This can be used to add additional mods, such as DynMap, to the server.

## Mod Removals in later versions of a pack

All containers have -Dfml.queryResult=confirm set, which means that in the event of any mod removals between versions, the change will be silently accepted.
