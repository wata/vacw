# VACW (vagrant-ansible-centos-wordpress)

This is a Vagrant configuration designed for development of WordPress plugins, themes, or websites.

## Preparations in advance

If you didn't install Homebrew

- Install `homebrew`

```sh
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

If you didn't install rbenv

- Install `rbenv` on `homebrew`

```sh
$ brew install rbenv
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
$ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.zshrc
$ brew install ruby-build
$ brew install rbenv-gemset
$ brew install rbenv-gem-rehash
$ exec $SHELL -l

# Install ruby
$ rbenv install 2.2.2
$ rbenv global 2.2.2
```

If you didn't install pyenv

- Install `pyenv` on `homebrew`

```sh
$ brew install pyenv
$ echo 'export PYENV_ROOT="${HOME}/.pyenv"' >> ~/.zshrc
$ echo 'if [ -d "${PYENV_ROOT}" ]; then' >> ~/.zshrc
$ echo '    export PATH=${PYENV_ROOT}/bin:$PATH' >> ~/.zshrc
$ echo '    eval "$(pyenv init -)"' >> ~/.zshrc
$ echo 'fi' >> ~/.zshrc
$ exec $SHELL -l

# Install python
$ pyenv install 2.7.10
$ pyenv global 2.2.2
```

If you didn't install AWS-CLI

- Install `awscli` on `pip`
- Create config file on `~/.aws/config`

```sh
$ pip install awscli
$ aws configure
# AWS Access Key ID [None]: XXXX
# AWS Secret Access Key [None]: XXXXXXXX
# Default region name [None]: ap-northeast-1
# Default output format [None]: text
```

## Getting Started

1. Install VirtualBox.

    from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

1. Install Vagrant.

    from [http://www.vagrantup.com/](http://www.vagrantup.com/)
    ```sh
    $ vagrant -v # e.g. Vagrant 1.7.2
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
1. Run `bundle install` to fetch all dependencies.

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
