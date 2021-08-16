## Discord OAuth2
#### Step 1
**You**: Redirect **User** to [https://discordapp.com/api/oauth2/authorize]()

###### Query Params
|name|value|
|:-:|:-:|
|client_id|Your application's Client ID|
|scope|A list of scopes, delimited by spaces|
|redirect_uri|The uri to send the user after authorization|

#### Step 2
**Discord**: Redirect **User** to `redirect_uri`

###### Query Params
|name|value|
|:-:|:-:|
|code|Temporary code for requesting access token|

#### Step 3
**You**: `POST https://discordapp.com/api/oauth2/token`

> *"Form Data" means the body must be sent as `application/x-www-form-urlencoded`*

###### Form Data
|name|value|
|:-:|:-:|
|client_id|Your application's client id|
|client_secret|Your application's client secret|
|code|Temporary code for requesting access token|
|grant_type|`"authorization_code"`|
|redirect_uri|The uri to send the user after authorization|

###### Response JSON Data
|name|value|
|:-:|:-:|
|access_token|Token used to make api requests as user|
|refresh_token|Token used to get a new access token|
|expires_in|Expiry time relative to now in seconds|
|scope|List of scopes the access token has|

### Refreshing an access token
**You**: `POST https://discordapp.com/api/oauth2/token`

###### Form Data
|name|value|
|:-:|:-:|
|client_id|Your application's client id|
|client_secret|Your application's client secret|
|refresh_token|Refresh token for desired user|
|grant_type|`"refresh_token"`|
