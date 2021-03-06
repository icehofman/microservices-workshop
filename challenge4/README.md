## Solution to Challenge 3

1. The influx container can be started with the scripts provided in _challenge4/influx_
2. Start the serialization service with the script _challenge4/serializer/run.sh_ (or _run.bat_)
3. Start the frontend with a script that has the following contents:
```sh
#!/bin/bash
export SERIALIZER_HOST=127.0.0.1
export SERIALIZER_PORT=10000
export FRONTEND_PORT=10001
npm start
```

4. Open the frontend at [http://localhost:10001/]()
5. Send some test data using the script _challenge4/serializer/testWrite.sh_ (or _testWrite.bat_)
6. The data points should appear on the frontend chart

## Challenge 4
![image](../images/fuge-logo.png)

Right now we only have 3 moving parts in our system, but already it is becoming
a pain to manage. Your challenge is to get the system running using Fuge. Fuge
is a microservice development environment that helps ease the process of local
development running processes and docker containers.

The folder _challenge4/fuge_ contains two files:

* compose-dev.yml - a docker compose format file that specifies the processes that make up our system
* fuge-config.json - global fuge settings

Your challenge is to run the system using the fuge shell. You can find some
documentation on fuge [here](https://github.com/apparatus/fuge). Once you
have the system started, you can check that everything is working by using the
script _challenge4/serializer/testWrite.sh_ (or _testWrite.bat_). You should see
data coming through to the frontend chart.

__hint__ you will need to stop all of the previously running processes and containers first. You may need to delete the influx container as well (`docker rm influx`).

__hint__ make sure that you have installed fuge using `npm install -g fuge`.

__hint__ you can start the fuge shell using the `fuge shell` command

__Note__ with docker 1.12 there are issues related to fuge and setting up a proxy correctly. Therefore, please start the influx container outside of fuge and start each of the services using the start command: `start serializer` and `start frontend`. 


## Next Up: [Challenge 5](../challenge5/README.md)
