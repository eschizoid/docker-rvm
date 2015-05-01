# Docker Base Image RVM preinstalled

[![tzenderman/docker-rvm](http://dockeri.co/image/tzenderman/docker-rvm)](https://registry.hub.docker.com/u/tzenderman/docker-rvm/)

Super easy to use & lightweight Docker image that comes with RVM for managing ruby versions. Docker Hub Link: https://registry.hub.docker.com/u/tzenderman/docker-pyenv-rvm-nvm/

## Want to use this in your project?

Simply add

`FROM tzenderman/docker-rvm:latest`

to the top of your Dockerfile and that's it. You'll now have rvm pre-installed in your container. Want to manage your ruby version in your project's repo? Simply add a `.ruby-version` file to your project's root and then manage the install inside your project's Dockerfile like this:

    WORKDIR /code

    COPY .ruby-version /code/.ruby-version
    COPY .gemrc /code/.gemrc
    COPY Gemfile /code/Gemfile
    RUN rvm install $(cat .ruby-version) && \
        rvm use --default && \
        /bin/bash -l -c "bundle install;"

Now, when you want to upgrade to a new language version, simply update your .ruby-version to `2.2.2`, rebuild your Docker image, and that's it!

Links:

RVM: https://rvm.io/
