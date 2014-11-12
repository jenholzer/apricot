# Neura API Documentation

## Authentication

You can query the Neura API to pull information about a user. All requests for user data must include an authorization header with the value containing the user's access token:

```
Authorization: Bearer asdf1234*****************
```

## API Root Endpoint

The current version of the Neura API is V1 and each call to the V1 API will start with:

 **https://wapi.theneura.com/v1**

## GET /users/profile/daily_summary

Get's a user’s wellness information for a single day. Requires a **Bearer** authorization token.

### Query Parameters
#### Required
- date: Date of the summary to retrieve in YYYY-MM-DD format
#### Optional
- source: The source device to retrieve data for. For example, if Neurosky device data is requested then this parameter should be set to "Neurosky".
### Headers
#### Required
- authorization: Bearer authorization token
 
 ### Example

```http
GET https://wapi.theneura.com/v1
```