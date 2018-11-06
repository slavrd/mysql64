## Packer mysql64 vagrant box
A packer project that creates a vagrant box, for virtualbox provider, with intsalled mysql.

#### Prerequisites:
* Install packer - [instructions](https://www.packer.io/intro/getting-started/install.html)
* Install virtualbox - [instructions](https://www.virtualbox.org/wiki/Downloads)

#### Building the box:
Run: `packer build template.json` and wait for the build to finish.
The vagrant box will be genereated in the current directory, named ubuntu-1604-vbox.box

#### Running Kitchen test:
* **Prerequisites:**
  * Install rbenv - `brew install rbenv`
  * Initialize rbenv - add to `~/.bash_profile` line `eval "$(rbenv init -)"`
  * Run `source ~/.bash_profile`
  * Install ruby 2.3.1 with rbenv - `rbenv install 2.3.1` , check `rbenv versions`
  * Set ruby version for the project to 2.3.1 - `rbenv local 2.3.1` , check `rbenv local`
  * Install bundler - `gem install bundler`
  * Install gems from Gemfile - `bundle install`
  * Add the box to vagrant - `vagrant box add --name  mysql64 --provider virtualbox ubuntu-1604-vbox.box`
  
* **Runnig Kitchen:**
  * List kitchen environment - `bundle exec kitchen list`
  * Build kitchen environment - `bundle exec kitchen converge`
  * Run kitchen tests - `bundle exec kitchen verify`
  * Destory kitchen environment - `bundle exec kitchen destroy`
  * Automatically build, test, destory - `bundle exec kitchen test`
