# Docker image with Bombard stress testing tool

This repo contain .Dockerfile for automatic build, configure and run of server stress testing tool - "Bombard"

http://blog.modsaid.com/2014/04/stress-testing-with-siege-and-bombard.html

It generally uses provided file with testing urls and tries to connect to these urls and measures response time etc.
It automatically creates graphs from results.

The command to build this container:
```
docker build -t bombard .
```

The command to run this container looks like this:
```
docker run -t -i -v $(pwd):/data bombard
```
Some folder is needed to be mounted inside the container to `/data` folder and this folder must contain `test_urls.txt` with one url per line.
Created graphs and outputs are located in this folder too.

Default configuration of bombard is and can be changed in the docker run command:
`bombard  -f /data/test_urls.txt -i50 -r10 -s100 -t10`

* start with 100 concurrent users
* runs for 10 times
* 50 concurrent users are added every run
* one test run takes 10 minutes
