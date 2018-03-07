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
