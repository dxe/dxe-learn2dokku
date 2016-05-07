Learn to Dokku
==============

This is a DxE Tech getting started guide for deploying with [Dokku](https://github.com/dokku/dokku). Dokku is a piece of software you can install on your server to let you deploy code using Git. It determines what type of environment to build by inspecting your code and applying a [buildpack](http://dokku.viewdocs.io/dokku/deployment/buildpacks/) based on what it sees. For instance, a repo containing a `package.json` file will get detected by the Node JS buildpack and install the necessary components for things to work. In most cases you also need a [Procfile](https://devcenter.heroku.com/articles/procfile) to tell Dokku the entrypoint of your app.

Dokku is written in Bash, and buildpacks contain Docker images. You can also make your own buildpacks and plugins.

[Read the docs](http://dokku.viewdocs.io/dokku/installation/). Maybe not all at once, but reference it to help you learn how things work.


Steps
-----

First, clone this repo. Make sure your ssh key has been [added to Dokku](http://dokku.viewdocs.io/dokku/deployment/user-management/) by a DxE Tech admin.

Next, open your terminal, `cd` into this directory, and add Dokku as a git remote. Replace `my-name` with your first and last name.

    git remote add dokku dokku@warpcannon.net:my-name

Then `git push dokku master`.

Visit `http://my-name.warpcannon.net` in the browser (replacing `my-name` with your name).

You should see page letting you know it worked. Congrats!

You can also run some Dokku commands to look around. To see a list of apps on the server, run:

    ssh dokku@warpcannon.net apps

To see all of your options, run:

    ssh dokku@warpcannon.net

License
-------

Copyright © 2016 Alex Gleason <alex@alexgleason.me>
This work is free. You can redistribute it and/or modify it under the
terms of the Do What The Fuck You Want To Public License, Version 2,
as published by Sam Hocevar. See the COPYING file for more details.
