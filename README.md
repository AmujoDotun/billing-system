## THis is the psudo-code solution to the question sent to my mail

** making 10 000 API calls at once might kill your CPU/RAM, if you don't have lots of it and It's not a good practice

**I would run 20 API calls asynchronously, when done, continues with the next 20, till all the billing is done

## Let get down to the procedure.

=> First query 20 users

=> Loop through those 20 users(20 users per batch @ 1.6sec is possible because we using asynchronously)

=> Make an asyn call to the API for billing those 20 users(Using asyn means you making all your request at once but one request is not waiting for another request to complete before it start)




