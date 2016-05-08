Learn to Dokku
==============
This is a DxE Tech getting started guide for deploying with [Dokku](https://github.com/dokku/dokku). Dokku is a piece of software installed on the DxE Tech server to let you deploy code using Git.

How Dokku Works
---------------
1. Dokku is installed on the server and listening for git repositories to be pushed to it.
2. When Dokku receives a git repository, it will begin the deploy process.
3. Dokku scans your codebase against the [buildpacks](http://dokku.viewdocs.io/dokku/deployment/buildpacks/) it knows about.
4. If there's a match, Dokku will continue with that buildpack.
5. A virtual, self-contained environment is built for your app using Docker, and it's based on the buildpack.
6. Dokku connects your app to an Nginx router installed on the server.
7. Deployed!

There's a little more between; there are some special files Dokku will scan for and use if available. Custom buildpacks can be made, and you can also use Dockerfiles instead of buildpacks for complex setups. The entire system is configurable and flexible.


Testing it out
--------------
Let's learn how to use Dokku by pushing this repo to it. The `.static` file in the root is used to associate this app with [buildpack-nginx](https://github.com/dokku/buildpack-nginx). Inside the `www` directory is a static site that we will try to deploy.

First, clone this repo. Make sure your ssh key has been [added to Dokku](http://dokku.viewdocs.io/dokku/deployment/user-management/) by a DxE Tech admin.

Next, open your terminal, `cd` into this directory, and add Dokku as a git remote. Replace `my-name` with your first and last name.

    git remote add dokku dokku@warpcannon.net:my-name

Then `git push dokku master`.

Visit `http://my-name.warpcannon.net` in the browser (replacing `my-name` with your name).

You should see a page letting you know it worked. Congrats! 🎉

### Other apps
What about apps that aren't static, like Python or Node.js apps? Just [find the relevant buildpack](https://github.com/dokku/) and set up your project to work with it. In many cases, all you will need is a `Procfile`. Make a file called `Procfile` in the root of your app, and make it say:

    web: <your executable> <app entrypoint>

For instance, a Python (Flask) project:

    web: gunicorn dxe_chapters_map.server:app

Or a Node.js project:

    web: node lib/server.js

Dokku will automatically detect a Python project by a `requirements.txt` file in the root, and a Node.js project by a `package.json` file in the root. Just add a Procfile and you're done!

Read the [Dokku docs](http://dokku.viewdocs.io/dokku/) to learn more. If you're wondering if Dokku can do something, it probably can.

### Shell commands
You can also run some Dokku shell commands to look around. To see a list of apps on the server, run:

    ssh dokku@warpcannon.net apps

To see all of your options, run:

    ssh dokku@warpcannon.net

License
-------
Copyright © 2016 Alex Gleason <alex@alexgleason.me>
This work is free. You can redistribute it and/or modify it under the
terms of the Do What The Fuck You Want To Public License, Version 2,
as published by Sam Hocevar. See the COPYING file for more details.
