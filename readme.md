## Shiny App Deployed on Docker

This project contains the following files:

 ### Dockerfile
 This dockerfile configures to use the docker image from this URL:https://hub.docker.com/r/rocker/shiny-verse
 And then loads all the necessary libraries including shiny dashboard and server

 The image is configured to expose port 8080 to which the shiny-server is connected

 ### shiny-server.conf

Shiny Server is an open source software to host your Shiny applications. All the configuration related information for Shiny server is added in shiny-server.conf file. For e.g.;

* site_dir configuration specifies the directory that contains Shiny applications and other web assets (HTML files, CSS files, etc.)
You place Shiny applications inside this directory to be invoked by the user. For instance, a Shiny application stored in 
`/srv/shiny-server/myApp` would be available at http://localhost:8080/myApp 
You could also place HTML files in this directory to make them available on your server, as well.

### shiny-server.sh
This shell executable file is used by the docker to create the necessary directories, set permissions and then finally start the shiny server

### app.R

This is the main Shiny app. 

### Building the docker image

Docker is a tool that is used to automate the deployment of applications in `containers` so that applications can work seamlessly in different operating systems and environments with no changes to the application.

From the terminal navigate into the root of this folder and key in the below command

* `cd ~` - this command will take you to your home folder
* `cd shiny` - if you are in the homefolder, you can now navigate to the root of shiny application with this command - assumes you cloned the shiny application in your home folder
* `docker build -t mydashboard .` - this command will build your docker image with the name mydashboard
* `docker run -d -p 8080:8080 mydashboard` - start the shiny app with this command