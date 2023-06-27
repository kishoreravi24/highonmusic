#### Let me cook.... , stay tuned something big i.e winter is coming 🥶


## High on Music , a music streaming application

### High on Music is an initializr for the ServiceGatewayHub the 3 magic words, Service discovery, api gateway, load balancer.

### Architecture
![highonmusic drawio](https://github.com/kishoreravi24/highonmusic/assets/36214175/eb0818de-f539-4518-9c5b-31580b4f6cde)


#### This Repo is a microservice contains Service discovery (eureka), ApiGateway (spring cloud api gateway) and loadBalancer (nginx) for the application.

#### Setting up of service discovery (microservice) with eureka server, with this eureka server we can register all our microesrvices like songs, podcast, playlist.
#### [service discovery eureka](https://github.com/kishoreravi24/highonmusic-serviceDiscovery)

#### Api gateway(microservice) with spring cloud api gateway, eg: user microservice running on port 8001, playlist on 8002 with api gateway we can run 

Api gateway:

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

#### Load balancer (nginx) : two replica of song service, podcast service, playlist service. Eg: In use of song servive when traffic is high it switches to replica service.


### Application works
#### [Songs microservice](https://github.com/kishoreravi24/highonmusic-songs) -> Here we have the route and logic + db for the songs used in our high on music application.
#### [Playlists microservice](https://github.com/kishoreravi24/highonmusic-playlists) -> Here we have the route and logic + db for the playlist used in our high on music application.
#### [Podcasts microservice](https://github.com/kishoreravi24/highonmusic-podcasts) -> Here we have the route and logic + db for the podcasts used in our high on music application.
