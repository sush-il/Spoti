# spoti

###### So far this is what i've learnt
###### we got to login url which redirects us to spotify authrize page with the given credentials and scope
###### This returns a code which can be used to get the acess token; code is in the url
###### we grab the code from the url
###### set credentials such as form, headers and authOptions; and use this to make a most request 
###### Once the post request is made we get back the access token and refresh token


##### So how i did it is with a button that goes to the calls the server port at /login 
##### The login redirects user to frontend (different port) with the auth code
##### The authcode is to receive the access token from the server
##### The access token is returned to the frontend. While trying to fetch data the access token is passed through the server port url as a param 
##### We access the access token from the url in the serer and use it get any data; then the data is passed back to the front end to be displayed

#### One of the big problem that i had at one point was the useEffect was doing a re-render automatically; was mounting twice for some reason on the homepage
#### This meant although all the data would load; the data (access token) we received from the server instantly became unusuable (it held the error, since the code used to get the token expired). 
#### The only solution i could think of was to actually remove the code from url after the first fetch; since code was now null access token fetch couldn't happen
