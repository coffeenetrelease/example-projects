# Starter Security Example Project

This is an example project to show the behaviour of the security starter.

You an starter this application with the following spring profile:

* `integration` will authenticate this application against the CoffeeNet Auth Server
* `development` will authenticate this application against local authentication

## Integration Profile

Please start the provided ldap and mariaDB docker containers with

```bash
./docker-compose up
```

Now on the CoffeeNet Auth Server is available with all its dependencies (ldap, mariaDB).

This example project is fully secure except of the http://localhost:8080/not-secure endpoints
that was made available for everyone through the `SecurityIntegrationConfiguration`.

If you want all endpoints to be secure, you do not have to create your own security configuration,
because by default all endpoints are secured. See the development profile example.

The endpoints http://localhost:8080 is still secure and needs authentication against the
**CoffeeNet Auth Server**.

```
Username: admin
Password: admin
```

defined by the ldap server.

#### Logout

CoffeeNet Auth Server on http://localhost:9999/logout and delete the cookie on localhost:8080


## Development Profile

Also in development mode the complete application is secure but not against the
CoffeeNet Auth Server rather against a local spring security with predefined users.

Admin user with COFFEENET-ADMIN & USER role:
```
Username: admin
Password: admin
```

Normal user with USER role:
```
Username: user
Password: user
```

as described in the security starters documentation.


#### Logout

Go to http://localhost:8080/logout