# Ibento

[![GitHub-CI Workflow Status](https://badgen.net/github/checks/Paul1365972/Ibento?label=Github%20Build&icon=github)](https://github.com/Paul1365972/Ibento/actions?query=workflow%3A%22Build%22)
[![CodeMC-CI Build Status](https://badgen.net/runkit/jenkins-status-vbryjbp7mcuc/ci.codemc.io%2Fjob%2FPaul1365972%2Fjob%2FIbento?label=CodeMC%20Build&icon=https%3A%2F%2Fsvgshare.com%2Fi%2FKEK.svg&cache=900)](https://ci.codemc.io/job/Paul1365972/job/Ibento/)

Ibento is the example fork of [Ilblu](https://github.com/Paul1365972/Ilblu).
It contains all patches I could find, that add upon the event api. If you find more or want to add your own just create an issue or pull request!

## Get Ibento

### Download

- [**Github Actions**](https://github.com/Paul1365972/Ibento/actions?query=workflow%3A%22Build%22)

### Plugin API

**[WIP]**

**Maven**
```xml
<repository>
    <id>codemc-snapshots</id>
    <url>https://repo.codemc.io/repository/maven-snapshots/</url>
</repository>

<dependency>
    <groupId>io.github.paul1365972</groupId>
    <artifactId>ibento-api</artifactId>
    <version>1.15.2-R0.1-SNAPSHOT</version>
    <scope>provided</scope>
</dependency>
```

**Gradle**
```groovy
repositories {
    maven {
        url "https://repo.codemc.io/repository/maven-snapshots/"
    }
}

dependencies {
    compileOnly "io.github.paul1365972:ibento-api:1.15.2-R0.1-SNAPSHOT"
}
```

This also includes the Paper-, Spigot- and Bukkit-API

### Build

#### Requirements

- Java (JDK) 8 or above
- Maven
- Git, with a configured user name and email. 
  On windows you need to run from git bash.

#### Compile

If all you want is a paperclip server jar, just run:
```sh
./gradlew paperInit paperApply paperclip
```

## Fork

Creating a fork via Ilblu has several advantages:
- Modular inclusion of other forks
- More modern framework for developing than older solutions (E.g byof)
- Incremental building

### Getting started

1. Fork this project
2. Edit `gradle.properties` to your likings
3. Add your fork name to the end of `/patches/apply`
4. Run ```./gradlew paperInit paperApplyPatches paperRebuildPatches```
5. (Edit the README.md)

### Add patch modules

Create a new folder/symlink in `/patches` containing the api and server subdirectories

Now add the name of the path to the patches folder above your fork in `/patches/apply`.

*Only use valid folder names; no dots, slashes, asterisks etc.*

### Keep in sync

Since Ilblu is patched frequently to stay up to date with [Paper](https://github.com/PaperMC/Paper), keeping your fork in sync is important to get any new features as soon as they come out. Choose any way you prefer:

- Sync Ilblu (Recommended): `./gradlew paperSync`

- Only update Paper: `./gradlew paperMergeUp`

- Do it by manually. Not sure how? [GitHub Help - Syncing a Fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)

## Developing

To get started clone this repository and run `./gradlew paperInit paperApplyPatches` or `./ilblu patch init` to setup your workspace.

### Creating patches

- Make changes to `/<NAME>-API` or `/<NAME>-Server` and commit them
- Run `./gradlew paperRebuildPatches` or `./ilblu rebuild`  to create the patch files
- Finish by committing and pushing the changes made to the patch files

### Testing

**Important: Test jars contain copyrighted material and should be distributed under no circumstances**

To build your test server jar just run ```./gradlew shadowJar```, output in `/<NAME>-Server/build/libs`

### Deploying

To get a distributable server jar (paperclip), just run ```./gradlew paperclip```, output in main directory

### Still confused?

Just head over to the example project [Ibento](https://github.com/Paul1365972/Ibento).

Creating and editing patches is explained in great detail over at [PaperMC](https://github.com/PaperMC/Paper/blob/master/CONTRIBUTING.md).

*Side note: Rebasing will be one of your best friends when creating patches, be sure to understand it well.*

## LICENSE

See [LICENSE](LICENSE)

Everything in this repository is free to be used in your own fork, except when noted otherwise. 

See list above for the license of material used/modified by this project.
