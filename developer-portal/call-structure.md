## Call structure

Your call to the Surfsight API should appear similar to:

    curl --request {httpMethod} 'https://api-prod.surfsight.net/{apiVersion}/{apiEndpoint}'
    --header 'Authorization: {token}'

The base URL is https://api-prod.surfsight.net/{apiVersion} for North
America and https://api.de.surfsight.net/{apiVersion} for Europe, with
v2 being the default API version.

The API call includes the following:

  ---------------------------------------------------------------------------------------
  Component       Description                 Example                          Location
  --------------- --------------------------- -------------------------------- ----------
  HTTP method     The action you want to      GET                              request
                  perform                                                      

  URL             The Surfsight API URL       https://api-prod.surfsight.net   request

  API version     The version of the          v2                               request
                  Surfsight API you are                                        
                  calling                                                      

  API endpoint    The API endpoint you want   /devices/{imei}/events           request
                  to reach                                                     

  Authorization   The [authentication         1234567                          header
                  token](#N1622535612653) in                                   
                  the Authorization header of                                  
                  your call                                                    
  ---------------------------------------------------------------------------------------