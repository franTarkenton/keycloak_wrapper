## Keycloak wrapper

This is a Python library, based on **Python3** which calls Keycloak API endpoints. It'

## Installation
`$ pip install keycloak_wrapper`

## Requirements
- [Python 3](https://www.python.org/download/releases/3.0/)
- [certifi==2018.1.18](https://pypi.python.org/pypi/certifi)
- [chardet==3.0.4](https://pypi.python.org/pypi/chardet)
- [idna==2.6](https://pypi.python.org/pypi/idna)
- [requests==2.18.4](https://pypi.python.org/pypi/requests)
- [urllib3==1.22](https://pypi.python.org/pypi/urllib3)

## Author
- [Panagiotis Kapsalis](https://www.linkedin.com/in/panagiotis-kapsalis-774800129/)

## Documentation

**Get Access Token**

With the following function a user who is registered on a Keycloak realm can take an access token. This function can executed from **any keycloak user**

Parameters
- KEYCLOAK_URL: http(s)://KEYCLOAK:{port}/auth
- REALM_NAME: Provide keycloak realm name
- CLIENT_NAME: Keycloak client name
- CLIENT_SECRET: Keycloak client secret
- USERNAME: keycloak username
- PASSWORD: keycloak password
```python
from keycloak_wrapper import access_token
token = access_token(KEYCLOAK_URL, REALM_NAME, CLIENT_NAME,CLIENT_SECRET, USERNAME, PASSWORD)
```
The response which is returned is the following:

```
{
   "access_token":{access-token}
   "expires_in": 300,
   "refresh_expires_in": 1800,
   "refresh_token": 
   "token_type": "bearer",
   "not-before-policy": 0,
   "session_state": {session-state}
}
```
**Refresh Access Token**

With the following function a user can refresh his access token. This function can executed from **any keycloak user**

Parameters
- KEYCLOAK_URL: http(s)://KEYCLOAK:{port}/auth
- REALM_NAME: Provide keycloak realm name
- CLIENT_NAME: Keycloak client name
- CLIENT_SECRET: Keycloak client secret
- REFRESH_TOKEN: Refresh token, the user gets a refresh token when he takes an access token
```python
from keycloak_wrapper import refresh_token
new_token = refresh_token(KEYCLOAK_URL, REALM_NAME, CLIENT_NAME,CLIENT_SECRET, REFRESH_TOKEN)
```
**Get well known KEYCLOAK endpoints**

With the following function a user can receive the keycloak's well known endoints. This function can executed from **any keycloak user**

Parameters
- KEYCLOAK_URL: http(s)://KEYCLOAK:{port}/auth
- REALM_NAME: Provide keycloak realm name
- ACCESS_TOKEN: Keycloak user access token
```python
from keycloak_wrapper import well_known
well_known_urls = well_known(KEYCLOAK_URL, REALM_NAME,ACCESS_TOKEN)
```
**Get user info**

With the following function, a user providing his access token can receive some information about his profile. This function can executed from **any keycloak user**

Parameters
- KEYCLOAK_URL: http(s)://KEYCLOAK:{port}/auth
- REALM_NAME: Provide keycloak realm name
- ACCESS_TOKEN: Keycloak user access token
```python
from keycloak_wrapper import user_info
info = user_info(KEYCLOAK_URL, REALM_NAME,ACCESS_TOKEN)
```
**Access Token Introspection**

With the following function, providing an access token, we can examine if the access token belongs on a registered keycloak user, if the token is valid. If the token is valid returns extended information about the user. This function can executed for **any keycloak user**.

Parameters
