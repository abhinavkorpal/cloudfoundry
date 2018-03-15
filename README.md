# cloudfoundry
This repo contain the work on cloudfoundry

# how to install and setup cloudfoundry in ubuntu

wget -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -

echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list

sudo apt-get update

cf login

API endpoint> https://api.run.pivotal.io

Email> 

Password>

# About Clodu Foundry

An open-source Platform-as-a-Service for running orchestrated polyglot application in an public or private environment.

polyglot means it can support number of languages so i can deploy them all to the same place.

It's orchestrated, so it's coordinated work, it's healthy monitored

cf api

cf spaces

cf create-space testing

cf space development

cf quotas

cf target -s testing

create a service instance :

cf marketplace

cf create-service mongolab sandbox mymongo

mongolab service i wanted
sandbox is plan 
mymongo is name of the instance

cf services

# Creating YAML :

Cloudfoundry works on the heroku buildpack model 

# During deployment: 

Cloud controller create records, tell the cloud controller to create a record for the application in its local database.

Cloud controller store some of the metadata, the application name, how many instance this should have who is the user was, what buildpack it's using.

It stores the application filesin blob store, cloud controller stores app files.

Appl start command issued.

Cloud controller chooses the staging DEA

Staging DEA caches package

Cloud controller chooses runtime DEA

# Deploying Application via CLI:

cf push <appname>

cf push <appname> --no-manifest

cf push <appname> -i 2

# Scaling:

cf scale <appname> -m 512M

cf scale <appname> -k 1G

cf scale <appname> -i 2

cf apps

cf app ps-seo-helloworld

cf files ps-seo-helloworld

cf files ps-seo-helloworld /app/log.txt

# Logs:

cf files ps-seo-helloworld /logs

cf logs ps-seo-helloworld --recent

cf events ps-seo-helloworld

# environment variable:

cf set-env <app> <variable name> <variable value>

cf unset-env <app> <variable name>

cf env ps-seo-helloworld

cf set-env helloworld ENVIRONMENT prod

# blue and green deployment:

cf push hellworld-stage -n hellworld-stage

cf map-route hellworld-stage cfapps.io -n hellworld

cf unmap-route hellworld-stage cfapps.io -n hellworld

cf app hellworld-stage

--Zero downtime when upgrading can be accomplished with blue-green deployments.
--Distribution of traffic is controlled by the percentage of app instances per version against the total number of app instances bound to the route.

--Serializing ObjectsL: if using Serializing Objects, don't make destructive changes. e.g: don't remove fields, do have a serialVersionUID

--Admin Processes: Run admin/mgmt tasks as one-ff processes. e.g: migrating data

--Database: Do make changes idempotent. e.g: copy data to a new field (don't delete data)
            No destructive database changes allowed. e.g: don't drop a column
            Do have backwards compatible changes. e.g: nullable fields


# Manifest Concept:

 cf | grep manifest

 cf create-app-manifest helloworld -p ./manifest.yml
 
 # Application security group:

 - Are virtual firewall that control egress/outbound traffic for application
 - Droplet is actually build with in the container
 
 cf security-groups
 
 cf security-group credhub-internal-z2
 
 cf running-security-groups
 
 cf unbind-running-security-group all_open
 
 cf create-security-group
 
 cf bind-security-group
