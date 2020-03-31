# OAuth2 Implementation with LDAP Backend

Uses [oryd/hydra](https://github.com/ory/hydra) and [icoreru/werther](https://github.com/i-core/werther) to provide an authentication platform for OAuth2 clients.

## Environment Variables

```properties
LDAP_URI=192.168.0.1:389             # LDAP Server and Port
LDAP_BINDDN=cn=admin,dc=domain,dc=tld # DN for Auhorised LDAP Binding
LDAP_BINDPW=Secret.123                # Password for Auhorised LDAP Binding
LDAP_BASEDN=dc=domain,dc=tld          # LDAP Base DN
LDAP_TLS=true                         # Use TLS/STARTTLS
WERTHER_LDAP_ATTR_CLAIMS=cn:name,sn:family_name,givenName:given_name,mail:mail
                                      # Attribure Mappings
CALLBACK=http://localhost:3000        # OAuth2 Callbacks
CALLBACK_LOGOUT=http://localhost:3000/post-logout-callback
CLIENT_ID=test-client                 # OAuth2 Client ID
CLIENT_SECRET=test-secret             # OAuth2 Client Secret
OAUTH_URL=http://localhost            # Base URL for OAuth2/Hydra
```

## Testing

http://localhost:4444/oauth2/auth?client_id=test-client&response_type=token&scope=openid%20profile%20email&state=12345678

You will need to modify the call based on your client ID, eg.

http://localhost:4444/oauth2/auth?client_id=${CLIENT_ID}&response_type=token&scope=openid%20profile%20email&state=12345678

If you have not built anything that listens on http://localhost:3000 then expect to see "unable to connect" following a successful authentication.

## Help

I've dumped out the `werther -h` help file so you can see what varaibles are available:

[werther_help](./werther_help)