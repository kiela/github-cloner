# Dockerize [GithubCloner](https://github.com/mazen160/GithubCloner) project

## Docker image

### Public

Public docker image of [GithubCloner](https://github.com/mazen160/GithubCloner) project is hosted on Docker Hub under [kiela/github-cloner](https://hub.docker.com/r/kiela/github-cloner/) slug. In order to pull the latest image from Docker Hub, use following command:

```
$ docker pull kiela/github-cloner
```

### Build

Build is done automagically by Docker Hub and gets triggered with every git push. However, if for some reason, you want to build docker image buy yourself, use following command inside clone `github-cloner` project:

```
$ docker build -t github-cloner .
```

## Usage

Please read [documentation of GithubCloner](https://github.com/mazen160/GithubCloner/blob/master/README.md) project first. Make sure you get yourself a [Github Personal Access Token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) as you will need it to use GithubCloner project. Once, you get it, use following command to run docker container and use GithubCloner:

```
$ docker run -t \
  -rm \
  --mount type=bind,source="$(pwd)"/output,target=output \
  github-cloner \
  -org organization-name \
  -a github-login:github-personal-access-token
```

##### NOTE:
By default all repositories are cloned into `/output` direcory inside docker container. In order to be able to use cloned repositories outside of docker container, we use [bind mount](https://docs.docker.com/engine/admin/volumes/bind-mounts/#start-a-container-with-a-bind-mount) Docker feature and amount `./output` directory from current directory as a `/output` directory inside docker container.

## Credits

All credits goes to [@amazen160](https://github.com/mazen160) who is  author of [GithubCloner](https://github.com/mazen160/GithubCloner) project.