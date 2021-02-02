_fastlane_ can be installed multiple ways. The preferred method is with _bundler_. _fastlane_ can also get installed directly through with Homebrew (if on macOS). Technically, you can use macOS's system Ruby but it's not recommended unless you are experienced Ruby developer.

#### Managed Ruby environment + Bundler (macOS/Linux/Windows)

**Ruby**

Please don't use system Ruby when possible. [There is a variety of ways to install Ruby without having to modify your system environment](https://www.ruby-lang.org/en/documentation/installation/). For macOS and Linux, _rbenv_ would be one of the most popular way to manage your Ruby environment.

You can use Ruby 2.4 - 2.7. Verify that you have a current version of Ruby installed:

```sh
$ ruby --version
ruby 2.7.2p137 (2020-10-01 revision 5445e04352) [x86_64-darwin19]
```

**Bundler**

It is recommended that you use `bundler` and `Gemfile` to define your dependency on _fastlane_. This will clearly define the used _fastlane_ version, and its dependencies, and will also speed up using _fastlane_.

- Install _bundler_ itself by `gem install bundler`
- Create a `./Gemfile` in the root directory of your project with the content
```ruby
source "https://rubygems.org"

gem "fastlane"
```
- Run `bundle update` and add both the `./Gemfile` and the `./Gemfile.lock` to version control
- Every time you run _fastlane_, use `bundle exec fastlane [lane]`
- On your CI, add `bundle install` as your first build step
- To update _fastlane_, just run `bundle update fastlane`

#### Homebrew (macOS)

This way you don't have to install Ruby separately and instead _homebrew_ install sthe best Ruby version alongside _fastlane_.
See [this page](https://formulae.brew.sh/formula/fastlane) for details.

```sh
brew install fastlane
```

#### System Ruby + RubyGems (macOS/Linux/Windows)

This is not recommended but you can still install _fastlane_ to system Ruby's environment. Using `sudo` often occurs unwanted results due to file permission and makes managing your environment harder.

```sh
sudo gem install fastlane -NV
```
