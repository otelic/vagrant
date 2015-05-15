This is a [veewee](https://github.com/jedi4ever/veewee) template for building a
[Vagrant](http://vagrantup.com/) box that closely mirrors our production
environment. You can build it yourself by following the directions below or install a prebuilt version from [here](URL to box on dropbox).

## Easy Install

Add the following to your `Vagrantfile`.

```ruby
Vagrant::Config.run do |config|
  config.vm.box = "otelic"
  config.vm.box_url = "URL to box on dropbox"
end
```

And run `vagrant up`. The box will be downloaded and imported for you.

## Building From Scratch

First, clone the repo and install gems with bundler.

```bash
$ git clone https://github.com/otelic/vagrant.git
$ cd vagrant
$ bundle install
```

Next, build the box with veewee. Go grab a cup of coffee because this is gonna
take a while.

```bash
$ bundle exec veewee vbox build otelic
```

And finally, install the box for use with Vagrant.

```bash
$ bundle exec veewee vbox export otelic
$ vagrant box add otelic otelic.box
```

Now all you have to do is setup vagrant in your project.

```bash
$ vagrant init otelic
$ vagrant up
$ vagrant ssh
```

## Included Packages

The packages that are included are carefully selected to closely match those on
the Celadon Cedar stack.

* Ubuntu 12.04 64bit
* Ruby 2.2.2 MRI
* RubyGems 2.4.7
* Python with pip, virtualenv, and virtualenvwrapper
* PostgreSQL 9.3.3
* NodeJS 0.12.3
* Foreman https://github.com/ddollar/foreman
