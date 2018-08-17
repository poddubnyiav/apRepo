#Task 
Start 3 instances of Artifactory on localhost. Deploy any file. Create Jmeter script that will get the file information and download it. 

# Presteps to run the test

1. Pull a docker image of artifactory OSS
```sh     
    docker pull docker.bintray.io/jfrog/artifactory-oss:latest
```     
2. Run 3 instances on localhost
```sh    
    docker run --name artifactory -d -p 8081:8081 docker.bintray.io/jfrog/artifactory-oss:latest
    docker run --name artifactory2 -d -p 8082:8081 docker.bintray.io/jfrog/artifactory-oss:latest
    docker run --name artifactory3 -d -p 8083:8081 docker.bintray.io/jfrog/artifactory-oss:latest
```
3. Deploy Text.txt file from 'apJmeterScript' folder to a default 'example-repo-local' repository

# Steps to run the test
1. Open an 'artifactoryFile.jmx' script with Jmeter and hit 'Run' button. 
2. Or run it in no-gui mode 
```sh
    jmeter -n -t <pathToScript\artifactoryFile.jmx> -l <pathToResultFile\results.jtl>
```
Script is configured to generate 10 Users load and hold it for 10 minutes. 
Script is configured to owerride existing file while it's being downloaded in order to avoid creation of thousands file (can be changed).
