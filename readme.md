# Heroku Buildpack for Kibana

This buildpack downloads and installs Kibana into a Heroku app slug. It is a fork of [omc/heroku-buildpack-kibana](https://github.com/omc/heroku-buildpack-kibana), with some tweaks to the compile script to support Elasticsearch 5 / Kibana 5.

## Usage

    # Set this buildpack on your app
    $ heroku buildpacks:set https://github.com/mcnelson/heroku-buildpack-kibana -a (replaceme)

    # Configure kibana.yml ES user/pass/URL
    $ heroku config:set ELASTICSEARCH_URL=(replaceme) ELASTICSEARCH_USERNAME=(replaceme) ELASTICSEARCH_PASSWORD=(replaceme) -a (replaceme)

    # Create a Procfile to run the Kibana web server. 0.0.0.0 host seems to be necessary on Heroku.
    $ echo 'web: kibana --port $PORT -H "0.0.0.0"' > Procfile

    # Push the above to trigger a deploy
    $ git push heroku master

    # Verify and profit!
    $ heroku open
