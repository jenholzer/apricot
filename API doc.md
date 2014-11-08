
###Welcome to the Neura API
**Interacting with the Neura API**

You can query the Neura API to pull information about a user.  All requests for user data must include an authorization header with the value containing the user's access token:

    Authorization: Bearer asdf1234*****************

###Neura API calls
**`daily_summary`** gives the user’s wellness information on the day you specify with the `date` parameter.  

- `daily_summary` values are calculated using the data currently available to Neura.  Consequently, `daily_summary` values can change as the user syncs their devices and updates their dataset. 
- `daily_summary` is only available for complete days and not for the current day.

**Parameters**
**`date`**  You request data for this day in the format YYYY-MM-DD
**`source`** Use `source` to specify when you want user data from a single partner device.  As of October 2014, this parameter is only available for the Neurosky data partner via ````source = neurosky````. 


**Permission** ```dailyActivitySummary```

   URI https://wapi.theneura.com/v1/users/profile/daily_summary

**Example request**
In this example `daily_summary` call, the client is requesting data from September 30th, 2014 for the user with access token  `asdf1234**************************`.


    GET /v1/users/profile/daily_summary?date=2014-09-30 HTTP/1.1
    Host: wapi.theneura.com
    Authorization: Bearer asdf1234**************************
    Cache-Control: no-cache



###Response
**status**	
Neura returns whether your API call was a ````success```` or ````error```` 

####If status is a ````success```` Neura will return:
**timestamp**	
Neura returns the time when it sent the response in epoch time 

**data**	
The complex object of ````success```` response data. As of October 2014, Neura returns 0 if data is not available for any of the sub-objects.
*Note for mike & berman: how do other companies convey complex objects in their docs? data > stuff is a quick hack*  

**data > date**	
Neura echoes  the ````date```` in your Request parameter in the  in the format YYYY-MM-DD.   

**data > minutesWalk**	
Neura returns the number of minutes that the user was continuously active either running or walking while outside their home. 

 **data > steps**	
Neura returns the number of steps the user walked on ````date```` .   If a user has multiple step-counting devices then Neura the merges data.

**data > calories**	
Neura returns the amount of calories the user burned on ````date```` in kilocalories (kcal).
 
**data > heartRate**	
Neura returns the user's average heartRate on ````date```` 
As of October 2014, only available for users with Neurosky. 

**data > weight**	
Neura returns the user's average body weight on ````date```` in kilograms (kg). 

####If status is  ````error```` Neura will return:
**errors**	
Neura returns a human-intelligible message explaining any
If API call fails then error code and message

**errors > code **
Neura returns a snake_case string representing the error code.

** errors > message **
Neura returns a human-readable message describing the cause of the error.

--- Mike and berman left off here --
   sleepData	The complex object of sleep
      length	The length of sleep
      deepSleep	The total minutes of deep sleep
      lightSleep	The total minutes of light sleep
activityPlaces	The complex object of activities at work or workout 
    name	the address of the place or user’s custom name of the place
    steps	number of steps at place
    calories	number of calories at place
    heartRate 	heart rate measure at place
    numOfTimesInDay	the number of times user was at place or did workout today





----



**HOW TO BECOME A DATA CONSUMER**
Data consumers must register their company and apps with Neura .me via http://dev.theneura.com The registration process returns the following parameters for service integration:

**app_id**	
App ID for the OAuth process
**app_secret**
App secret for the OAuth process


USER AUTHENTICATION
Neura follows the OAuth flow described in The OAuth 2.0 Protocol (RFC 6749 ). SSL is required in OAuth flow.  The OAuth flow 2.0 request should be implemented via the consumer’s application integration with Neura.me SDK. Look at Neura.me SDK  The authentication process returns the following parameters:

access_token	
A token... 
Neura provides you with an access token specific to the user
grants you privileges for getting the user’s data
the token is unique the privileges that you are granted for the user: if your request for privileges changes then you may get a new token


MANAGING USERS
Neura events and services identify users via Neura user ID. The service “User” maps the user agent access token to Neura userId that is used in Neura push events and pull services.
User’s access token must be sent in the header.
The endpoint that returns general data about a user:

Your Request
GET https://wapi.theneura.com/v1/user
Authorization: Bearer <access_token>

Where: 
Your request Parameters
[None]
Your request Headers
Authorization 
 Neura will provide you with this access token during the OAuth flow. You must precede the access token with “Bearer” 

Neura’s response:
user_id	
Neura user identifier that is used in any Neura events and services
timezone	
The time zone that the user was in when they last updated Neura’s server.

Example: Your Request
GET https://wapi.theneura.com/v1/userHost: wapi.theneura.com
Authorization: Bearer asdf123***************************************

Example: Neura’s Response
	{
		user_id: usr234***,
		timezone: PLACE_HOLDER
}


...

Next to do’s
Berman & Mikimer: keep bringing over “NEURA.ME API Integration Guide ver 2”
Berman: keep providing code examples
Mikimer: keep ensuring the explanations make sense; go back and edit what we got formatted properly but haven’t yet edited.

For coordination:
Mike works from San Francisco Mon/Wed/Fri
Mike works from Sunnyvale Tues/Thurs -- so I must catch the train by 8.30am

Neura follows the OAuth flow as described in The OAuth 2.0 Protocol (RFC 6749 ), which requires. SSL is required in OAuth flow.  As of October 2014, Neura only offers authentication flow within a user’s phone and does not offer web-based authentication flow.  Consequently, for your app to authenticate with Neura, you must (1) embed the the Neura SDK in your app and (2) ensure that your user has the Neura app on their mobile device. As of October 2014, we provide details below for integrating with Neura’s Android SDK; Neura’s iOS SDK is not yet available.   The authentication process returns the following parameters:
