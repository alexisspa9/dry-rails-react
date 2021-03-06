[![codecov](https://codecov.io/gh/patrickclery/dry-rails-react/branch/master/graph/badge.svg)](https://codecov.io/gh/patrickclery/dry-rails-react)
![Rails + React + PostgreSQL](https://github.com/patrickclery/dry-rails-react/workflows/Rails%20+%20React%20+%20PostgreSQL/badge.svg)
![Dependabot Status](https://badgen.net/dependabot/patrickclery/dry-rails-react/?icon=dependabot)
![Docker Image](https://badgen.net/docker/size/patrickclery/dry-rails-react/latest/amd64)

## Getting Started

## Requirements

* PostgreSQL *or* Docker (depending which method you choose)

### Method #1: Running Rails on your machine

1. Clone this repo to your local machine:

```shell script
git clone https://github.com/patrickclery/amazon-asin.git
```

2. From the command-line, cd into the directory: 

```shell script
cd amazon-asin
```

 If you are using `rvm_autoupdate_flag=1` in your `~/.rvmrc`, this will automatically install Ruby 2.6.5. Otherwise, run it manually:
 
```shell script
 rvm install
```

_Note: Using RVM is optional, just make sure you have Ruby 2.6.5 available._ 

3. Run the setup script. This does several things:
- Installs bundler (if necessary)
- Installs the required ruby gems
- Prepares your database
- Seeds your database

```shell script
bin/setup
```

### Method #2: Docker

1. Fire up Docker on your local machine
2. Run this command to build and deploy the app:

```shell script
docker-compose --env-file=.env up
```

_Note: .env is generated by `bin/setup` but you can create one using the sample .env.sample_

3. Be sure that your Docker container publishes port 3000 (manually required).

### Method A: Running the Rails server on your system.

1. Fork the repo.

2. Run the setup script.

    ```shell script
    bin/setup
    ```
    This does several things:
    
    - Installs the required ruby gems and JavaScript packages.
    - Prepares your database:
        - Creates the databases
        - Seeds the data
    - Creates a .env file with default settings
    
3. Open the app in your browser by navigating to [http://localhost:3000/](http://localhost:3000/) 

### Method B: Docker

1. Fire up Docker on your local machine
2. Run this command to build and deploy the app:

    ```shell script
    docker-compose --env-file=.env up
    ```
    
    _Note: .env is generated by `bin/setup` but you can create one using the sample .env.sample_

3. Be sure that your Docker container publishes port 3000 (manually required).

4. Open the app in your browser by navigating to [http://localhost:3000/](http://localhost:3000/)

### Method C: Deploy to Heroku (in a Docker container)

1. Install heroku CLI on MacOS:

    ```shell script
    brew tap heroku/brew && brew install heroku
    ```

2. Deploy the app on Heroku (this requires a heroku.com account.) You will want to enable "Automatic Deploys" for your _master_ branch.

    ```shell script
    heroku git:remote -a your-heroku-subdomain-goes-here
    heroku stack:set container
    git push heroku master
    ```

3. The app should be up & running on your Heroku subdomain. If not, you can debug any errors by checking the build long (under the "Activity" tab on Heroku), or tailing the logs:

    ```shell script
    heroku logs --tail
    ```

## Features

- **GitHub Actions**
    - Docker images published on every commit to master branch (@via [docker build-push-action](https://github.com/docker/build-push-action))
    - RSpec tests run on every push
- **Dockerization**
- **Heroku Deployment** (using the Docker configuration)

## What is included?

#### These gems are added to the standard Rails stack

* Core
    * [better_errors](https://github.com/charliesome/better_errors) – useful error pages with interactive stack traces
    * [fast_jsonapi](https://github.com/Netflix/fast_jsonapi) – a JSON serializer that follows the standards of Google's JSON:API
    * [react-rails](https://github.com/reactjs/react-rails) – combines Rails + React + Webpacker. comes setup with a default App component at /
    * [rubocop](https://github.com/rubocop-hq/rubocop) – enforces Ruby code style
* Security
    * [brakeman](https://github.com/presidentbeef/brakeman) – detect security vulnerabilities
* Testing
    * [capybara](https://github.com/teamcapybara/capybara) – integration tests with screenshots
    * [codecov](https://github.com/codecov/codecov-ruby) – integration with [codecov.io](https://codecov.io/)
    * [faker](https://github.com/faker-ruby/faker) – generate fake data for tests
    * [shoulda](https://github.com/thoughtbot/shoulda) Common RSpec tests for Rails
    * [vcr](https://github.com/vcr/vcr) – save http requests for re-use with tests
    * [webmock](https://github.com/bblimke/webmock) – simulate live http requests

