# Services

Lokal provides software as sepatare `roles`. There the `lokal` role that installs, well, lokal base
services such as databases, minio (s3 compatible storage), prometheus and traefik (router).

## Lokal role

This is the only role that does not hold any software - it is intended solely for developers. You
will use it when add your own role (service). Common role contains logic to install, backup, restore, and remove
applications. Therefore it is hard-wired in playbook.yml because all standard roles are using it. If you
want to add a new software to Lokal stack please visit (lokal/)[this lokal role] for more information.

## Example role

The other special role is `_example_app`. Copy-paste this one to start creating your own.

## Other roles

All other roles contain installable software. Roles define their default variables in `default/main.yml`.
Roles can use undefined variables to force you to actually define them. This is not as lokal as before
because for example passowrds are deduced from `lokal_secret`. Only publically-facing credentials need to
be defined.

Each role should take advantage of `admin_password` to create any "admin" accounts if possible. If your
software is intended only for admin users and it doesn't have builtin authentication mechanism then you
can easily hide it behind traefik's basic authentication mechanism.

# Creating your own service

Please take a look in the `lokal` role that provides necessary logic for apps instalations and handling.
