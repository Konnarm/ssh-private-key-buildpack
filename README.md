# ssh-private-key-buildpack

A heroku buildpack for setting the ssh private key as part of the application build. It's meant to be used with [heroku-buildpack-multi](https://github.com/heroku/heroku-buildpack-multi), before other buildpacks which require the key to be present, like installing private repositories from `gitlab`.

# Example usage

Upload the private key to heroku.

```
heroku config:set SSH_KEY=$(cat ~/.ssh/id_rsa)
```

Add a `.buildpacks` file (used by `heroku-buildpack-multi`) which contains this and the default python buildpack.

```
https://github.com/anewbigging/ssh-private-key-buildpack.git
https://github.com/heroku/python
```

Now as long as the public key is present on gitlab and the user has the correct permissions, it's possible to install from private `gitlab` repositories.
