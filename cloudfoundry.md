cf push node -m 128M --random-route 

pivotal network

polymorphic platform

self serve platform and it allow to easily push an application

microservice based architecture and operstionally robust

cf logs articulate --recent

cf push articulate -p ./articulate/articulate-0.2.jar --random-route

cf logs articulate --recent

cf scale articulate -m 1G

cf logs articulate | grep "API\|CELL"

cf events articulate
