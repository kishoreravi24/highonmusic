## High on Music , a music streaming application

### Architecture
![highonmusic-design](https://github.com/kishoreravi24/highonmusic/assets/36214175/a3df804f-8e3d-4efa-ace0-0ddef98e56fd)

#### HighonMusic-users
* Users microservices - [link](https://github.com/kishoreravi24/highonmusic-users)
    * Postgres DB - currently I don't add the support for registering new user features. As an initial work, we are using the username and password as (test), you can check the application resources and DTO and DAO of this microservice for more details about username and password connectivity.
    * JWT token - For security purpose I added this JWT token got so much information about this do check the JWT service, main feature this generates the JWT token and we can use the token.

* UI - [link](https://github.com/kishoreravi24/highonmusic-ui)
    *  React - I created this UI with react and material-ui for css framework, not complex design just normal one, for more details check the apiCall.jsx to see the api calls and other information.
    *  Passing props - I used useContext for passing props as for the initial version, in future will upgrade to the Redux.
    *  port - 3000

* Service Discovery - [link](https://github.com/kishoreravi24/highonmusic-serviceDiscovery)
    * Setting up of service discovery (microservice) with eureka server, with this eureka server we can register all our microesrvices like songs, podcast, playlist.
    * Running on port 8671, with this we can see which microservice is up or not, but note: UI is separate from this.
* Api Gateway - [link](https://github.com/kishoreravi24/highonmusic-apigateway)
    *  Api gateway(microservice) with spring cloud api gateway, so below microservice runs on different port and different configuration, we need to specify CORS for each so instead , we can addresss all the microservice in Api gateway to use with one port: 5000.
    *  Eg: song-microservice running on port localhost:8081/songs,localhost:8082/podcasts if we configured this service with api gateway means we can use like localhost:5000/songs,localhost:5000/podcasts.
    *  We are providing LOAD - BALANCER feature also with spring-cloud-netflix-ribbon
    ```
      ribbon:
        eureka:
            enabled: true
        listOfServers: localhost:8081,localhost:8181
        ServerListRefreshInterval: 1000
    ```
##### we are using mongodb database to store songs, currently I didn't add the support for adding the songs, Just done the get part only.
```
_id: 64abb8a2428b49e4b16eee69
audio: "SUQzAwAAAANtK1RJVDIAAAAXAAAAQmFlIC0gTWFzc1RhbWlsYW4uZGV2AFRQRTEAAAAzAA…"
tag:
    Array 0:
    language: "tamil"
    movie: "Don"
    name: "Bae"
    preview: "https://c.saavncdn.com/295/Bae-From-Don--Tamil-2022-20220203163123-500…"
```
* Song microservice - [link](https://github.com/kishoreravi24/highonmusic-songs)
    *  JWT use, we are getting the token to check the user is logged in or not with restTemplate.
    *  we are getting the songs from the mongodb, for the info please check the application resource.
* Song-replica microservice - [link](https://github.com/kishoreravi24/highonmusic-songsreplica)
    * For load balancer use, created this mircroservice running on 8181, replica of the song microservices.
* Podcasts microservice - [link](https://github.com/kishoreravi24/highonmusic-podcasts)
    *  same as song microservices, we are using the podcasts db to fetch and this feature is in developing phase.
* Playlists microservice - [link](https://github.com/kishoreravi24/highonmusic-playlists)
    *   same as song microservices, we are using the playlists db to fetch and this feature is in developing phase.
