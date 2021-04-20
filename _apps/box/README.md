# PFHub App

Ensure that `cert.pem` and `1014649_e91k0tua_config.json` are in this
directory. Run with

Test the main site with

    $ curl -X "POST" -F "fileb=@./shell.nix" \
      https://pfhub-box.appspot.com/upload/ | \
      jq '.download_link' | xargs wget -O test.nix

Test the local site with

    $ nix-shell --pure
    [nix-shell]$ uvicorn main:app --reload

and then

    $ curl -X "POST" -F "fileb=@./shell.nix" \
      http://localhost:8000/upload/ | \
      jq '.download_link' | xargs wget -O test.nix

The code tests can be run with

    [nix-shell]$ py.test test.py

## Deploy to App Engine

    $ gcloud init
    $ gcloud app deploy

and

    $ gcloud app logs tail -s default

to observe the logs once deployed.
