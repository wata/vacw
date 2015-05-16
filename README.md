# VCCW (vagrant-chef-wordpress)

This is a Vagrant configuration designed for development of WordPress plugins, themes, or websites.

## Getting Started

If you didn't install Homebrew

```sh
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

1. Install VirtualBox.

    from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

1. Install Vagrant.

    from [http://www.vagrantup.com/](http://www.vagrantup.com/)
    ```sh
    $ vagrant -v # e.g. Vagrant 1.7.2
    ```

1. Install Ruby on Homebrew

    ```sh
    $ brew install rbenv
    $ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
    $ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
    $ brew install ruby-build
    $ brew install rbenv-gemset
    $ brew install rbenv-gem-rehash
    $ source ~/.bash_profile
    ```

1. Install Rake

    ```sh
    $ gem install rake
    ```

1. Clone this repository.

    ```sh
    $ git clone git@github.com:wata/vacw.git
    ```

1. Change into the new directory.

    ```sh
    $ cd vacw
    ```

1. Initial setup.

    ```sh
    $ rake init
    ```

1. Edit `Vagrantfile`.

    ```sh
    $ vi Vagrantfile
    ```

1. Creates and configures guest machines according to your `Vagrantfile`.

    ```sh
    $ vagrant up
    ```

1. Visit [http://wordpress.local](http://wordpress.local).


## Contribute

### Setting up

1. Clone this git repository on your local machine.
2. Run `bundle install` to fetch all dependencies.

### Running and writing tests

There is automated tests using [Serverspec](http://serverspec.org/).

The tests files are in the `spec/` directory.


Before running the serverspec tests, you'll need some dependencies.

```
$ bundle install --path=vendor/bundle
```

Then to run the tests, just execute following.

```
$ bundle exec rake spec
```
