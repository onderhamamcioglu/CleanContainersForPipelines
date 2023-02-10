# CleanContainersForPipelines
Cleaning docker containers in GitHub Actions pipelines.

```docker stop CONTAINER_ID``` simply stops a running container but you may need to pass container IDs to this container and doing this in pipelines is difficult.

You can find some solutions on forums like: ``` docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q) ``` but this will probably fail. The reason is GitHub Actions is looking for a variable called _"docker ps -a -q"_ but obviously this is not a variable, this is the command getting variables.

This problem is also mentioned [here](https://dev.to/saulsilver/docker-stop-all-processes-on-github-actions-533j) and the writer found the solution by writing a bash script.

I created this repo because writing and executing this script in a pipeline makes the pipeline .yaml look crowded. So you can just download, chmod and run the script by executing the following line in the pipeline.

```bash
wget https://github.com/onderhamamcioglu/CleanContainersForPipelines/releases/download/script/CleanContainersForPipelines.sh && chmod +x CleanContainersForPipelines.sh && ./CleanContainersForPipelines.sh
```


### Reference

[Hatem Houssein's solution on dev.to](https://dev.to/saulsilver/docker-stop-all-processes-on-github-actions-533j)
