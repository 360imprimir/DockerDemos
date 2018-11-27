Run the following command to create the image:
docker build -t dockerfiledemo3 .

Check the image created:
docker images

It should have the same size than the dockerfiledemo2.

Now change somtehing in the source code without changing the project or solution file, like add ";" somewhere in code.
Build the image again:
docker build -t dockerfiledemo3 .

In the output notice that all steps previous to "COPY . ." report that are using cache.

Now, let's try to run the container using the command (if in use, change the 9091 port to a free port on your machine):
docker run -it --rm -p 9091:80 dockerfiledemo3

Access http://localhost:9091 the application should answer.

If you press CTRL+C because of the --it parameter the application should stop running and the container will also stop.
And because of the --rm once the container stops it will be removed, you can check that the container no longer exists with the command:
docker ps -a