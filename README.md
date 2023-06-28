#### Let me cook.... , stay tuned something big i.e winter is coming 🥶


## High on Music , a music streaming application

### Architecture
![Screenshot 2023-06-28 at 5 28 32 PM](https://github.com/kishoreravi24/highonmusic/assets/36214175/69cc20fc-30a3-4650-a0b2-db99d4a833b5)

#### First layer contains, two microservices one is service discovery(eureka server and discovery client) used to register all microservices and we can see which are up and which are down, second is api-gateway(spring cloud api-gateway) to use all services in one instance or all in one use + we have load balancer(netflix ribbon) i can use replica server for each microservices to handle traffic.

### Service discovery

#### Setting up of service discovery (microservice) with eureka server, with this eureka server we can register all our microesrvices like songs, podcast, playlist.
#### [high on music service discovery](https://github.com/kishoreravi24/highonmusic-serviceDiscovery)

#### Api gateway(microservice) with spring cloud api gateway, eg: user microservice running on port 8001, playlist on 8002 with api gateway we can run 

### Api gateway

API Gateway takes all API requests from a customer, determines which services are demanded, and combines them into a unified, flawless experience for users. 

* Security for microservices
* Authentication, monitoring/metrics, and resiliency
* The client does not know about the internal architecture of our microservices system. The client will not be able to determine the location of the microservice instances.
* Simplifies client interaction as he will need to access only a single service for all the requirements.

1. parameter validation
2. Allow list / Deny list
3. Authentication / Authorization
4. Rate limit
5. Dynamic Routing
6. Portocol conversion - mainly for sending request and response <->
7. Circuit Breaker
8. Error Handling
9. Logging and monitoring
10. Analytics

[high on music api gateway](https://github.com/kishoreravi24/highonmusic-apigateway)

### Load balancer (netflix-ribbon) inside api-gateway 
Two replica of song service, podcast service, playlist service. Eg: In use of song servive when traffic is high it switches to replica service.


### Application works
#### [Songs microservice](https://github.com/kishoreravi24/highonmusic-songs) -> Here we have the route and logic + db for the songs used in our high on music application.
#### [Playlists microservice](https://github.com/kishoreravi24/highonmusic-playlists) -> Here we have the route and logic + db for the playlist used in our high on music application.
#### [Podcasts microservice](https://github.com/kishoreravi24/highonmusic-podcasts) -> Here we have the route and logic + db for the podcasts used in our high on music application.
