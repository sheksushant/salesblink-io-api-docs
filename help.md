Grab the slate image (docker pull slatedocs/slate) or build the docker image for the repository (docker build . -t slatedocs/slate).

Build Slate:
$ docker run --rm --name slate -v $(pwd)/build:/srv/slate/build -v $(pwd)/source:/srv/slate/source slatedocs/slate build

Run to Test:
$ docker run --rm --name slate -p 4567:4567 -v $(pwd)/source:/srv/slate/source slatedocs/slate serve

Build HTML Files:
$ bundle exec middleman build --clean

Help
https://github.com/slatedocs/slate/wiki/Using-Slate-in-Docker