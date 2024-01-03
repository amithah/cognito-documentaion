
# Cognito Commands

## User registration

Registers the user in the specified user pool and creates a user name, password, and user attributes.

```
aws cognito-idp sign-up \
  --client-id YOUR_USER_POOL_CLIENT_ID \
  --username YOUR_USERNAME \
  --password YOUR_PASSWORD \
  --user-attributes Name=email,Value=YOUR_EMAIL

```
Usage example 
```
aws cognito-idp sign-up --client-id 3n4b5urk1ft4fl3mg5e62d9ado --username jane@example.com --password PASSWORD --user-attributes Name="email",Value="jane@example.com" Name="name",Value="Jane"
```
Output
```
{
  "UserConfirmed": false,
  "UserSub": "e04d60a6-45dc-441c-a40b-e25a787d4862"
}
```
## Login
Initiates sign-in for a user in the Amazon Cognito user directory.

```
aws cognito-idp initiate-auth \
  --auth-flow USER_PASSWORD_AUTH \
  --auth-parameters USERNAME=YOUR_USERNAME,PASSWORD=YOUR_PASSWORD \
  --client-id YOUR_USER_POOL_CLIENT_ID

```
Usage example 
```
aws cognito-idp initiate-auth --auth-flow USER_PASSWORD_AUTH --auth-parameters USERNAME=jane@example.com,PASSWORD=PASSWORD --client-id 3n4b5urk1ft4fl3mg5e62d9ado
```
## User details retrieval
Retrieves detailed information about a specific user from the user pool.
## admin-get-user
Gets the specified user by user name in a user pool as an administrator. Works on any user.
```
aws cognito-idp admin-get-user \
  --user-pool-id YOUR_USER_POOL_ID \
  --username YOUR_USERNAME
```
Usage example 
```
aws cognito-idp admin-get-user --user-pool-id us-west-2_aaaaaaaaa --username jane@example.com
```
Output
```
{
  "Username": "4320de44-2322-4620-999b-5e2e1c8df013",
  "Enabled": true,
  "UserStatus": "FORCE_CHANGE_PASSWORD",
  "UserCreateDate": 1548108509.537,
  "UserAttributes": [
      {
          "Name": "sub",
          "Value": "4320de44-2322-4620-999b-5e2e1c8df013"
      },
      {
          "Name": "email_verified",
          "Value": "true"
      },
      {
          "Name": "phone_number_verified",
          "Value": "true"
      },
      {
          "Name": "phone_number",
          "Value": "+01115551212"
      },
      {
          "Name": "email",
          "Value": "jane@example.com"
      }
  ],
  "UserLastModifiedDate": 1548108509.537
}
```
## Access token retrieval

Retrieves detailed information about a specific user from the user pool.
```
aws cognito-idp initiate-auth \
  --auth-flow USER_PASSWORD_AUTH \
  --auth-parameters USERNAME=YOUR_USERNAME,PASSWORD=YOUR_PASSWORD \
  --client-id YOUR_USER_POOL_CLIENT_ID \
  --query 'AuthenticationResult.AccessToken'
```
Usage example 
```
aws cognito-idp initiate-auth --auth-flow USER_PASSWORD_AUTH --auth-parameters USERNAME=jane@example.com,PASSWORD=PASSWORD --client-id 3n4b5urk1ft4fl3mg5e62d9ado --query 'AuthenticationResult.AccessToken'
```