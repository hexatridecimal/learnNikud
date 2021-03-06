# Nikud Pronunciation Sound Collection App

This is a simple React app that allows multiple speakers to record all
the sounds for each nikud. A speaker has an ID and we add all
aleph-bet letters with each possible nikud combination.

[![Nikud Pronunciation Sound Collection App](http://img.youtube.com/vi/z1mszMaORAI/0.jpg)](http://www.youtube.com/watch?v=z1mszMaORAI "Nikud Pronunciation Sound Collection App")

## Data and Origin

We generated this data from the alephbet_with_nikud.json created by the
data import process described here:
https://github.com/hexatridecimal/learnNikud/tree/main/data

## Setup and Installation

First do the normal Rails housekeping to bootstrap the app.

```
bundle
bin/rake db:create
bin/rake db:migrate
```

Each speaker will need to have the following command ran for them.
Run the command to import the letters/nikud combinations into
the database.

```
bin/rake letters:import name=Yana --trace
```

You will get the edit URL that can be shared with the speaker. You will
see this something like: /letters/#4203e526eeeae7f6aaf4
This URL can be added to the main url of the app, for example:
https://myapp.mydomain.com/letters/#4203e526eeeae7f6aaf4
And the translator can be sent to this URL to do the recording work.

Dokku or Heroku deployment can be done by setting the dokku remote and
from the root of the repository running:

```
git subtree push --prefix data/pronunciation_recording_app  dokku master
```

You will also need to add the plugin for https support letsencrypt.

```
sudo dokku plugin:install https://github.com/dokku/dokku-letsencrypt.git
dokku letsencrypt:enable <appname>
```
