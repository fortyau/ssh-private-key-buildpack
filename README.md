# ssh-private-key-buildpack

A heroku buildpack for setting the ssh private key as part of the application build. It's meant to be used with [heroku-buildpack-multi](https://github.com/heroku/heroku-buildpack-multi), before other buildpacks which require the key to be present, like installing private `npm` modules from `github`.

# Example usage

Upload the private key to heroku (note that the key needs to be base64 encoded).

```
heroku config:set SSH_KEY=$(cat ~/.ssh/id_rsa | base64)
```

Use:

```
heroku buildpacks:set https://github.com/fortyau/ssh-private-key-buildpack
```

Now as long as the public key is present on github and the user has the correct permissions, it's possible to install `npm` modules from private `githup` repositories.
