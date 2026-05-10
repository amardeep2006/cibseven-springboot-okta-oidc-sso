# cibseven okta example
This example has cibseven webapps secured via okta ssso (OIDC - Authorization code flow) and engine rest via Client credentials flow. It also has legacy camunda apps that are secured via okta sso (Auth code flow).

Things to make sure in Okta app registration:

1. Both Authorization code and Refresh token grant types are enabled.
2. Login redirect URI are set to http://localhost:8080/webapp/sso-login.html (for new webapps) and http://localhost:8080/login/oauth2/code/okta (for legacy camunda webapp)
3. user demo@demo.com is created and has been assigned okta group camunda-admin
4. Under default authorization server --> default --> claims make sure to add following claims:
    ID Token:
        groups: matches regex .*
    Always include in token: true
    Access Token:
        groups: matches regex .*
    Always include in token: true

Note : This is Achieved via oficial starters from cibseven and identity is read only in this case. This means you cannot add users/ groups in cibseven database. All users/ groups are managed in Okta.

TO-DO : Authorization enabled for proper RBAC . Current configs are just for Authentication and okta based sso login.

This is based on the original cib seven springboot getting started repo.
