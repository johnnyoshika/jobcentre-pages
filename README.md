# Setup (Windows)
* With Scoop (recommended)
  * Install [Scoop](https://scoop.sh/)
  * Add `extras` and `versions` buckets:
    * `scoop bucket add extras`
    * `scoop bucket add versions`
  * Find all available ruby versions:
    * `scoop search ruby`
  * Install latest ruby from `main` bucket and version 2.5 from `versions` bucket:
    * `scoop install ruby ruby25`
  * Install `MSYS2`
    * `scoop install msys2`
    * `msys2`
    * When you see this:
    > This is first start of MSYS2. You MUST restart shell to apply necessary actions.
    * ...type `exit` <kbd>Enter</kbd>
  * Install the `MSYS2` and `MINGW` development toolchain
    * `ridk install`
    * When asked which components to install, just hit <kbd>Enter</kbd>. I believe it selects option `3` by default.
  * Check the ruby version:
    * `ruby --version`
  * Switch betweeen ruby versions
    * `scoop reset ruby` -> to latest version
    * `scoop reset ruby25` -> to version 2.5
  * Make sure you're on version 2.5:
    * `scoop reset ruby25`
* With direct installer (not recommended)
  * Install RubyInstaller: https://rubyinstaller.org/downloads/
    * Choose the Ruby+Devkit option
      * Choose v 2.5.X (e.g. `Ruby+Devkit 2.5.7-1 (x64)`)
      * 2.6+ (e.g. `Ruby+Devkit 2.6.5-1 (x64)`) was problematic on Windows 10 with computer 'Seville' on 2020-01-24 and I got the following error when running command `bundle install`
      ```
      ffi-1.9.25-x64-mingw32 requires ruby version < 2.6, which is incompatible with...
      ```
    * When prompted, enable MSYS2 installation
    * At the end, allow installer to initialize MSYS2 Devkit (`ridk install`)

# Setup (macOS)
* Update Homebrew: `brew update`
* Use Ruby version manager
  * Install rbenv if it isn't installed: `brew install rbenv`
  * Upgrade rbenv if it's already installed: `brew upgrade rbenv`
* Setup rbenv integration to your shell
  * `rbenv init`
* Install and use Ruby version 2.5.3
  * `rbenv install 2.5.3`
  * `rbenv global 2.5.3`

# Setup continued (All OS)
* Install bundler
  * `gem install bundler -v 1.17.1`
  * Note: Windows 10 and bundler version 2.0.1:
    * bundler version 2.0.1 (the default on 2019-01-23) on Windows 10 with computer 'Austin' didn't install, even though I saw the message `Successfully installed bundler-2.0.1`.
    * Running `bundle install` afterwards resulted in: `find_spec_for_exe': can't find gem bundler (>= 0.a) with executable bundle (Gem::GemNotFoundException)`
    * Installing bundler version 1.17.1 gets around this problem
* Clone this repo
* `cd` into this project folder
* Install gems
  * `bundle install`

# Development
* In the project directly, start the Jekyll server: `bundle exec jekyll serve`
* Go to http://localhost:4000

# Deployment
* Push to master branch on GitHub. This will trigger continuous deployment to update the remote site on Netlify.