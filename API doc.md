
##Welcome to the Neura API
**Interacting with the Neura API**

You can query the Neura API to pull information about a user.  All requests for user data must include an authorization header with the value containing the user's access token:

    Authorization: Bearer asdf1234*****************

Permissions - in Android & iOS SDK guides. Specific to each platform. 

##Neura API calls

###The `daily_summary` request
You can use the `daily_summary` request to get a user’s wellness information for a single day.  

- Neura calculates values for `daily_summary` using the current dataset for the user. However,  values may change as the user syncs their devices with Neura, which may update their dataset. 
- `daily_summary` is not available for the current day; it is only available for previous days.

**Request parameters**
   URI https://wapi.theneura.com/v1/users/profile/daily_summary
**`date`**  The specific day, in YYYY-MM-DD format, for which you want information. 
**`source`** The specific partner device for which you want information.  As of October 2014, this parameter is only available for the Neurosky device, `source = neurosky`. 

**Permission** ```dailyActivitySummary```

**Example request**
In this example `daily_summary`, the client is requesting data from September 30th, 2014 for the user with access token  `asdf1234*****************`.


    GET /v1/users/profile/daily_summary?date=2014-09-30 HTTPS/1.1
    Host: wapi.theneura.com
    Authorization: Bearer asdf1234**************************
    Cache-Control: no-cache



###The `daily_summary` response
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
