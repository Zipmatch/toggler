#Toggler#

##A Feature Toggle Micro Service written in Clojure##

###Docker###

There is a Docker file, if you use that you don't need to read the section below about "running"
the application / service.  You should, however take a look at the file README-Docker.md

###Standalone#########

If you grab a release and all you want to be worried about is having Java on the machine
you are going to run it on, then grab a "standalone" jar and run it like this:

java -jar toggler-[version number]-standalone.jar [/absolute/path/to/config/]

and the embedded Jetty will spin up on port 7000.

The releases were created on a machine running Java 1.8, I haven't tested them on 1.7 or
lower and make no guarantees that they will work.

The service has an example config, just so that the application has some example
"toggles" for you to play with.  It is in the root of the project "config.json" - you should
move it to a disk location that will be writable by the running application.

All you need to do is write your own config in valid JSON in the same structure and then PUT
it to the service on the /reconfigure endpoint.

##Using the Service##

I recommend [Postman][2] and [Insomnia][3], but grab the REST Client of your choice
and poke the API:

[2]: https://www.getpostman.com/
[3]: https://insomnia.rest/

    GET http://127.0.0.1:7000/toggle

and see all the default / example feature toggles.

    GET http://127.0.0.1:7000/toggle/app1

and see all the toggles for "app1"

    GET http://127.0.0.1:7000/toggle/app1/cache

and get the value of the "cache" feature toggle in "app1"

You can see where this is going, I hope...

There are PUT and POST options to add new components and toggles, and to save your new / current
config, even to load other configs have a play around with it, that's the best way to explore.

