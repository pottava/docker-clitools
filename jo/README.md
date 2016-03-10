Supported tags and respective `Dockerfile` links:  
・latest ([jo/versions/0.7/Dockerfile](https://github.com/pottava/docker-clitools/blob/master/jo/versions/0.7/Dockerfile))  
・0.7 ([jo/versions/0.7/Dockerfile](https://github.com/pottava/docker-clitools/blob/master/jo/versions/0.7/Dockerfile))  

# Usage

`docker run --rm pottava/jo -p $(env)`
`docker run --rm pottava/jo -p -a spring summer fall winter`
`docker run --rm pottava/jo time=$(date +%s) dir=$HOME`
