# Getting Started

This guide specifically covers the process of getting Bullet Train up and running on your local machine so you can start developing your application. If you've just purchased Bullet Train, be sure to see the [overview of first steps as a new Bullet Train customer](https://blog.bullettrain.co/so-youve-bought-bullet-train-whats-next/).

As an optional prerequisite, please read our blog article describing [how and why Bullet Train is distributed the way it is](https://blog.bullettrain.co/how-is-bullet-train-distributed/).

## 1. Install Dependencies
Before you can get started with Bullet Train, you must have the following dependencies installed:

 - Ruby 2.7
 - Redis 6.0
 - PostgreSQL 13
 - [Chrome](https://www.google.com/search?q=chrome) (for headless browser tests)

Internally, Bullet Train is developed on macOS and these dependencies (other than Chrome) are installed using [RVM](https://rvm.io/) and [Homebrew](https://brew.sh) like so:

```
brew install postgresql
brew services start postgresql
brew install redis
brew services start redis
rvm install ruby-2.7.2
```

## 2. Clone (Don't Fork) The Repository
First, [create a new private repository on GitHub](https://github.com/new). (Please be careful that the repository you create is actually private, since otherwise you would be redistributing Bullet Train. 😬)

Once you have the new repository ready, clone our repository to your local machine.

```
git clone git@github.com:bullet-train-co/bullet-train-tailwind-css.git your-new-app-name
cd your-new-app-name
git remote rename origin bullet-train
git remote add origin git@github.com:your-username/your-new-app-name.git
git push origin main
```

In those steps you've renamed the original Bullet Train repository to be referred to as `bullet-train` and your own repository is now your `origin`. (This means you'll be able to merge in updates from `bullet-train/main`.)

Using GitHub's "Fork" feature is only for developers when they want to submit a Pull Request to the Bullet Train codebase. It's _not_ the correct way to get started building a new project with Bullet Train.

## 3. Run Bundler and Yarn
As with any Rails app, you'll need to run `bundle install` and `yarn install`.

## 4. Name Your Application
Run `bin/set-name "Whatever Your App Name Is"` to properly configure your database name, session store, and application class name. This tool will spit out some additional instructions as well.

## 5. Set Up Your Database
Run `rake db:create`, `rake db:migrate`, and `rake db:seed` to get your database into working condition. If you install PostgreSQL the way described above, this should work automatically. If it fails to connect, you'll need to configure your database in whatever way you normally do for Rails development.

## 6. Create Local Environment Configuration
Copy `config/application.yml.example` to `config/application.yml` as a baseline for your application configuration.

## 7. Start the Server
Start the server with `rails s` and visit `http://localhost:3000/`. The first time you render the sign-in page the stylesheets will take a few seconds to compile. Don't worry, it'll cache them going forward. Your application is now up and running and you can test the sign-up process.