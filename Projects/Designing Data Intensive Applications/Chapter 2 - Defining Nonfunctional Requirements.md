Functional Requirements: Functionality that your application must offer, what screens and what buttons you need, and what each operation is supposed to do in order to fulfill the purpose of your software.

Nonfunctional requirements: Eg. App should be fast, reliable, secure, legally compliant, and easy to maintain. 

Case Study: Social Network Home timeline
Assume
1. users make total of 500 million posts per day, or 5800 posts per second on average
2. Peak: 150000 posts per second
3. average user follows 200 people and has 200 followers

Representing users, posts and follows:
1. Keep data in relational database
2. Users, posts, follow relations table

Naive Approach:
1. Use the follows table to get a list of everyone the current user is following
2. Get the most recent posts from the followed users
3. Posts are timely, so assuming after someone makes a post, we want the followers to be able to see, we need to run this query every 5 secs (polling). 
4. Assume 10 mil users online and logged in, we need to run this query 2 mil times per second
5. Also, we will need 200 * 2 mil = 400 mil lookups per second for the average case.

How to make this better:
1. Instead of polling, it would be better is the server actively pushed new posts to any followers who are currently online
2. Precompute the results of the query so that a user's request for their home timeline can be served from a cache
3. Keep a data structure that keeps the home timeline of a user. Whenever someone posts, we look up all the followers and insert that post into the home timeline of each follower. When the user logs in, we simply query from this home timeline
4. Assume a rate of 5800 posts per second, if avg post reaches 200 followers, we have to do about a 1 milllion home timeline writes per second. Much better than 400 mil reads we would have to do.

Defining performance:
1. Response time: the elapsed time from the moment when a user makes a request until they receive the requested answer. 
2. Throughput: The number of requests per second, or the data volume per second, that the system is processing. For a given allocation of hardware resources, there is a maximum throughput that can be handled.
3. For social network home timelines: posts per second and timeline writes per second are the throughput metrics, whereas time it takes to load the home timeline and time until a post is delivered to followers are response time metrics.