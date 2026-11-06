# website-no-ai
Website and blog made with no AI

## Local development

Use Ruby 3.3.11 and Bundler 4.0.9, as recorded in `.ruby-version` and
`Gemfile.lock`. Ruby 2.6 (the macOS system Ruby) is too old for this bundle.

On Apple Silicon with Homebrew:

```sh
brew install ruby@3.3 llvm
export PATH="$(brew --prefix ruby@3.3)/bin:$PATH"
gem install bundler -v 4.0.9
```

Then install the gems and start the site:

```sh
MAKEFLAGS="CXX=$(brew --prefix llvm)/bin/clang++" bundle install
bundle exec jekyll serve
```

The `MAKEFLAGS` setting selects Homebrew LLVM when Bundler compiles
`eventmachine`; this avoids build failures when the installed Apple command-line
compiler is older than the active macOS SDK. On other platforms, `bundle install`
should work with a supported Ruby 3.2 or newer.

