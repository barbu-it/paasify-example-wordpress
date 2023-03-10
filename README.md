<p align='center'>
<img src="https://github.com/barbu-it/paasify/raw/develop/logo/paasify_project.svg" alt="Paasify Project">
</p>

# Paasify Project Wordpress

This paasify project deploys a wordpress instance. This project includes:

* Wordpress: Blogging instance based on php-fpm and mysql
* Traefik: Used as HTTP proxy
* Homepage: Dashbord to list installed services

You will need have a working [Paasify](https://github.com/barbu-it/paasify) instance to run this project.

| :exclamation:  This project is not meant to be deployed straight on production, please adapt and secure this project depending your needs. This project is provided as learning material.  |
|-----------------------------------------|


## Tutorial

This quick guide should help you to deploy this project locally.

### Install Paasify

If you don't have a working `paasify` instance or if you want to install the project paasify version, you can install a dedicated instance into a python virtualenv:
```
python3 -m venv .venv
. .venv/bin/activate
pip install paasify
paasify --version
```

### Deploy this project

To deploy this project, your must first checkout the project with git and go into the directory:
```
git clone https://github.com/barbu-it/paasify-example-wordpress.git wordpress
cd wordpress
```

As this project contains a database, an admin and user database password must be provided. The passwords can be edited in the `secrets.yml` file:
```
$EDITOR secrets.yml
```

Eventually you check or edit `paasify.yml` configuration:
```
$EDITOR paasify.yml
```

Your project is now configured, let's deploy it!

### Deploy stacks

Install project dependencies
```
paasify src install
```

Deploy your project:
```
paasify apply
```

You can check your stacks are properly running with:
```
paasify ps
```

By default, you can access to your dashboard on the http url: [http://home.localhost/](http://home.localhost/)

### General workflow

When you are happy with your first deployment, you can start to edit your `paasify.yml` configuration, then build your changes with `paasify build`. You can check what actually changed with git commands:

1. Make this project your
    1. If you want to put this project into your infrastructure, you will want to fork this repo.
1. Make changes
    1. `nano pasify.yml`: Modify your project config
    1. `paasify build`: Build `docker-compose.run.yml` files
    1. `git status -sb`: Show all modified files
    1. `git diff`: Show changes
    1. `paasify apply`: Test and apply changes
    1. If you are happy with your changes, continue; otherwise restart this section until you're happy with your changes
1. Validate changes
    1. `git add`: Add validated changes into git stage
    1. `git commit`: Commit validated changes
    1. `git push`: Push upstream your changes. IMPORTANT: There is NO secret management in paasify, and before this feature is available, be sure you understand security implications of comitting secrets into git repos.

## Informations

Paasify documentation is available [here](https://barbu-it.github.io/paasify/).

Created by mrjk for [Paasify](https://github.com/barbu-it/paasify). This work is licensed under GPLv3 license.
 
