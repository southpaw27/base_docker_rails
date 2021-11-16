This whole setup is inspired by the https://semaphoreci.com/community/tutorials/dockerizing-a-ruby-on-rails-application
blog post.

Small additions and changes, as well as a base implementation of Devise auth have been made.

This is a bare bones rails project and that can be cloned and used to setup a new project quickly.

After cloning the repository, run:
```
docker build -t rails-toolbox \
       --build-arg USER_ID=$(id -u)  \
       --build-arg GROUP_ID=$(id -g) \
       -f Dockerfile.rails .
```
This builds the docker image


Next, if you really want to start from scratch, run:

```
rm -rf ./yourappname
```

This will remove the base rails project from this directory.

To start a completely new rails project, run:

```
docker run -it \
    -v $PWD:/opt/app \
    rails-toolbox rails new --skip-bundle yourappname
```

The will generate a new rails project with yourappname as the directory name


run 

```
rm -rf yourappname/.git
```
if the top level directory already has a .git file

You will need to create the docker volumes:
```
$ docker volume create --name yourappname-postgres
$ docker volume create --name yourappname-redis
```

