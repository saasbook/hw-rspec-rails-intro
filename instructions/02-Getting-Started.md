# Getting Started

## Key concept: the code we wish we had

We will write unit and module-level tests using RSpec.  (RSpec can also be used for integration tests, but we prefer Cucumber for that task since it facilitates dialogue with the customer and automates acceptance as well as integration tests.)  RSpec is a domain-specific language (DSL) for testing Ruby code.  A DSL is a small programming language designed to ease tackling problems within a single area (domain) at the expense of generality.  You've already seen examples of external (standalone) DSLs, such as HTML for describing Web pages. RSpec is an _internal_ or _embedded_ DSL: RSpec code is just Ruby code, but takes advantage of Ruby's features and syntax so as to make up a "mini-language" focused on the job of testing.  Regular expressions are another example of an internal DSL embedded in Ruby.

RSpec's facilities help us capture _expectations_ of how our code should behave.  Such tests are executable specifications or "specs" written in Ruby, hence the name RSpec.

As the text notes, to capture expectations in tests before there is any code to be tested, we write a test that exercises the _code we wish we had_. This step forces us to think not only about what the code will do, but how it will be used by its callers and collaborators (other pieces of code that have to work with it).


In the rest of this exercise we will use TDD to develop the RottenPotatoes functionality that allows a user to look up a movie in TMDb.  Specifically, we will use TDD to create the controller method, which receives the user's request, and the model method, which actually calls the remote TMDb service to get information about the specified movie.

## Setup
Start by cloning this assignment's starter repository:

```
git clone git@github.com:cs169/su24-chips-8.5-<TEAM NUMBER>.git rspec-rails-intro
cd rspec-rails-intro
```

Make sure your Bundler version is <2.0 (`gem uninstall bundler`, then `gem install --version=1.17.3 bundler` if you have the wrong version installed). Then, run `bundle install --without production` to set up all the dependencies.

Onwards! In this assignment we will be working with the TMDb API and Guard to automate our workflow. We also make use of [Faraday](https://github.com/lostisland/faraday) - an HTTP client library - to make API calls. So, go ahead and edit the `Gemfile` to include the following gems:

```ruby
gem 'faraday', '1.8.0'  # in main group; simplifies calling TMDb
group :test do
  gem 'rails-controller-testing'
  gem 'guard-rspec'                 # automates re-running tests
end
```

* Rerun `bundle install` to get the gems.  Then run `rails generate rspec:install` to ensure the files needed by RSpec are in place.

* Edit the file `spec/rails_helper.rb` to include `require 'byebug'` at the top, so we can drop into the debugger as needed to get tests working.

* Later we will introduce the Guard tool as a way to re-run tests automatically as you code.  Run `bundle exec guard init rspec` to setup the files necessary for Guard, which will result in a new `Guardfile` being created; add that file to your repo.

* Setup the database with the usual commands:

```
bundle exec rails db:migrate
bundle exec rails db:seed
```

* Use this command whenever you want to run the server:

```
bundle exec rails server -b 0.0.0.0
```

---

[← Intro to RSpec and TDD](01-Intro-to-RSpec-and-TDD.md) | [Contents](README.md) | [Part 1: TDD drives creating route, view, and controller method →](03-Part-1--TDD-drives-creating-route--view--and-controller-method.md)
