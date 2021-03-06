FATE Stand-alone Deployment Guide
=================================

The stand-alone version provides three deployment methods, which can be
selected according to your actual situation:

-  Install FATE using Docker `Chinese
   guide <./doc/Fate-standalone_deployment_guide_zh.md>`__
   *(Recommended)*

-  Install FATE in Host `Chinese
   guide <./doc/Fate-standalone_deployment_guide_zh.md>`__

1) Install FATE using Docker\ *(Recommended)*
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

It is strongly recommended to use docker, which greatly reduces the
possibility of encountering problems.

1. The host needs to be able to access the external network,pull the
   installation package and docker image from the public network.

2. Dependent on `docker <https://download.docker.com/linux/>`__ and
   `docker-compose <https://github.com/docker/compose/releases/tag/1.24.0>`__,
   docker recommended version is 18.09, docker-compose recommended
   version is 1.24.0, you can use the following command to verify the
   docker environment: docker –version and docker-compose –version,
   docker start and stop and other Please refer to: docker –help.

3. Check whether the 8080, 9060, and 9080 ports are occupied before
   executing. If you want to execute again, please delete the previous
   container and image with the docker command.

   please follow the below step:

::

   #Get code
   FATE $ wget https://webank-ai-1251170195.cos.ap-guangzhou.myqcloud.com/docker_standalone-fate-1.4.0.tar.gz
   FATE $tar -xzvf docker_standalone-fate-1.4.0.tar.gz

   #Execute the command
   FATE $ cd docker_standalone-fate-1.4.0
   FATE $ bash install_standalone_docker.sh

   #Validation results
   FATE $ CONTAINER_ID=`docker ps -aqf "name=fate_python"`
   FATE $ docker exec -t -i ${CONTAINER_ID} bash
   FATE $ bash ./federatedml/test/run_test.sh

There are a few algorithms under
`examples <../examples/federatedml-1.x-examples>`__ folder, try them
out!

You can also experience the fateboard access via a browser:
Http://hostip:8080.

2) Install FATE in Host
^^^^^^^^^^^^^^^^^^^^^^^

1. Check whether the local 8080,9360,9380 port is occupied.

   ::

      netstat -apln|grep 8080
      netstat -apln|grep 9360
      netstat -apln|grep 9380

2. Download the compressed package of stand-alone version and decompress
   it.

   ::

      wget https://webank-ai-1251170195.cos.ap-guangzhou.myqcloud.com/standalone-fate-master-1.4.0.tar.gz
      tar -xzvf  standalone-fate-master-1.4.0.tar.gz

3. Enter FATE directory and execute the init.sh.

   ::

      cd standalone-fate-master-1.4.0
      source init.sh init

4. Execution test.

   ::

      cd standalone-fate-master-1.4.0
      bash ./federatedml/test/run_test.sh

There are a few algorithms under
`examples <https://github.com/FederatedAI/FATE/tree/master/examples/federatedml-1.0-examples>`__
folder, try them out!

You can also experience the fateboard access via a browser:
Http://hostip:8080.
