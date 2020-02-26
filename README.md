## THis is the psudo-code solution to the question sent to my mail

** making 10 000 API calls at once might kill your CPU/RAM, if you don't have lots of it, and It's not a good practice even though you have lot of cpu

## Method I'm using in this psudo-code
**I would run 20 API calls asynchronously, when done, continues with the next 20, till all the billing is done

## Let get down to the procedure.

=> First query 20 users

=> Loop through those 20 users(20 users per batch @ 1.6sec is possible because we using asynchronously)

=> Make an asyn call to the API for billing those 20 users(Using asyn means you making all your request at once but one request is not waiting for another request to complete before it start)


##  Based on the time lag of 1.6sec for a single user
**  10,000 users should take about 4.5 hrs to bill them. while
** While 100,000 users will take about 44.5 hrs

## Last Opinion

let's assume that we have 2 secs to make each request, I'm approximating 1.6s now (we could have network latency)
that means we can make about 1,800 trips to the API  under an hour (3600 / 2) 3600sec = 1hr

then we need to spread out the number of user billed per two seconds equally, between the 1800 trips
that would be approximately 6 users per batch

let's test:

in every 2 seconds, we bill 6 users

since there are 1800 of 2 seconds in hour, that means we can process 6* 1800 users in an hour 
+ 10800 users/ per hour

Don't let forget that the process or approched used here is Asynchronously meaning all request are taking place at the sametime.

Thank you.