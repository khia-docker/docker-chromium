Chromium browser in Docker
==========================

If you ever wonder how to run chromium in Docker.
This docker image might be a solution.
The need to run chromium in Docker is helpfull for deployment testing.
For example you might have another docker image running with your app configured to use specific DNS name.
Usual way to test this is to update `/etc/hosts` on your host to redirect to localhost.
However you cannot use this technique in the case when standard ports are already used on your host.
This Dockerfile could be used to solve the problem (not yet working this way).
It does work as a browser in docker though.

Installation
------------

    docker pull diet/docker-chromium
    docker run diet/docker-chromium cat /app/bin/chromium.run > ~/bin/chromium.run && chmod +x ~/bin/chromium.run
    docker run diet/docker-chromium cat /app/bin/enable_video > ~/bin/enable_video && chmod +x ~/bin/enable_video
    docker run diet/docker-chromium cat /app/bin/enable_sound > ~/bin/enable_sound && chmod +x ~/bin/enable_sound
    docker run diet/docker-chromium cat /app/bin/enable_camera > ~/bin/enable_camera && chmod +x ~/bin/enable_camera

Basic usage
-----------

    chromium.run ~/.local/.chromium/work &

Tips
----

You might want to create wrapper scripts in `~/bin` something like `chromium.work` and `chromium.personal`. Which would call `chromium.run` with appropriate directory.

TODO
----

Find a way to produce single script on host. Rather than using 4 scripts.

Acknowledgements
----------------

This work is based and inspired by

  - Dockerfile of Daniel Mizyrycki <daniel@docker.com>
  - Running Google chrome in a container post from https://www.stgraber.org/category/planet-canonical/
  - Special thank you to @tsutsu for the idea
