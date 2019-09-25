# 【Mac】How to set up Ruby on Rails development environment

## Install Homebrew
### Installing the Xcode
You should install the Xcode from App store

### Installing Command Line Tools
```:Terminal
$ xcode-select --install
> xcode-select: note: install requested for command line developer tools
```
A software update popup window will appear, and please choose to confirm this by clicking “Install”, then agree to the Terms of Service when requested.

### Installing Homebrew
Homebrew is the most popular package manager for Mac OS X.
Please paste following script in a Terminal, and press Enter:
``` :Terminal
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### Checking whether `Homebrew` is installed
Run the following command to check whether `homebrew` is installed.
``` :Terminal
$ brew doctor
```
It is success if it outputs 'Your system is ready to brew.'


## Install Ruby
### Installing rbenv
rbenv is a tool that you install multiple versions of Ruby and switch Ruby versions.

Run the following command to install `rbenv`
``` :Terminal
$ brew install rbenv
```
Next, you have to check whether `rbenv` is installed.run the following command to check whether `rvenv` is installed.
``` :Terminal
$ rbenv --version
2.2.3 (set by ******)  //  you will see latest version here at that time.
```

### Installing ruby-build
ruby-build is plugin of rbenv provided `rbenv install` so that it install Ruby of different version.

Run the following command to install `ruby-build`
``` :Terminal
$ brew install ruby-build
```

### Output 'eval "$(rbenv init -)"' to the bash_profile
Run the following command
``` :Terminal
$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
$ source ~/.bash_profile
```

### Installing Ruby
Run the following command to install 'Ruby' version 2.6.3.
``` :Terminal
rbenv install 2.6.3
```

### Change version of Ruby
Run the following command to change version of 'Ruby'
``` :Terminal
$ rbenv global 2.6.3
$ rbenv rehash
$ ruby -v
> ruby 2.6.3 // (You success if you will see specified number at ruby global)
$ gem -v
> 3.0.1
```

## Install bundler
### Installing bundler
Bundler provides a consistent environment for Ruby projects by tracking and installing the exact gems and versions that are needed.

Run the following command to install bundler with gem
``` :Terminal
$ gem install bundler
```

Also, you have to check installed bundler
``` :Terminal
$ bundle -v
> Bundler version 2.0.2 // you will see latest version here at that time.
```

## Install Rubyh on Rails
### Making a workspace direcotory and application directory
``` :Terminal
$ ls ~/

Run the following command if you don't exist workspace directory
$ mkdir ~/workspace

$ cd ~/workspace
$ mkdir rails_practice // `rails_practice` is an example, so you must name a directory. 
$ cd rails_practice 
$ mkdir first_app  // `first_app` is an example, so you must name a directory.
$ cd first_app
```
> ## About linux command
> * `mkdir` command - `make directory` -  you can make a new directory.
> * `li` command -  `list` - you can see list of directory an file in the specified directory.
> * `cd` command -  `change directory` - you can change the current directory to the specified directory.

### bundle init
Run the following command to generates a Gemfile into the current working directory
``` :Terminal
$ bundle init
> Writing new Gemfile to /Users/*****/workspace/rails_practice/first_app/Gemfile
```

### Changing Gemfile
Open the Gemfile with texteditor, and you should remove comment out `gem "rails"`. Also, you can specify the Rails versions.
This example specified the rails version `5.2.3`.
``` :Gemfile
source "https://rubygems.org"

gem 'rails', '~> 5.2.3'
```

### Installing Ruby on Rails
Run the following command to install Ruby on rails.
``` :Terminal
$ bundle install --path vendor/bundle
Fetching gem metadata from https://rubygems.org/...........
```

###  Generate Rails applications
Run the following command to generate Rails application.
``` :Terminal
$ bundle exec rails new .

```

### Installing the libraries
``` :Terminal
$ bundle install --path vendor/bundle
Fetching gem metadata from https://rubygems.org/...........
```

### Start up Rails application
``` :Terminal
$ bin/rails s
```
Next, you should access to `http://localhost:3000` with browser, and 
you success if browser page show the following url's image.
https://railsguides.jp/railsguides/images/getting_started/rails_welcome.png

