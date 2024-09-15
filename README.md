# Overleaf registration worker

Public user registration for a self-hosted
[Overleaf](https://github.com/overleaf/overleaf) CE instance.

## Use

A simple form (available on `/register` path) is offered to the user asking for its email;
the application then logs into the Overleaf instance with the administrator account
and sends a request to create a user.

The user can now create an account by clicking the confirmation link on its mailbox.

## Deployment

There is a Docker image available on
[ghcr.io/RobbyV2/overleaf-registration](https://ghcr.io/RobbyV2/overleaf-registration),
automatically built by GitHub Actions.
You can check the example `docker-compose.yml` file and tweak it with your configuration.

It is recommended to use a reverse proxy such as nginx,
to route the application on the /register path overriding
the default overleaf route.

### Environment variables

The Docker container needs all the following environment variables to function properly:

| Environment variable | Description                                          |
|----------------------|------------------------------------------------------|
| `HCAPTCHA_SITE_KEY`  | HCaptcha Site Key                                    |
| `OL_INSTANCE`        | Overleaf self-hosted instance (without trailing `/`) |
| `OL_ADMIN_EMAIL`     | Overleaf administrator account email                 |
| `OL_ADMIN_PASSWORD`  | Overleaf administrator account password              |

## Credit

Thank you to [StudentiUniMi](https://github.com/StudentiUniMi/overleaf-registration) for the original source code.
