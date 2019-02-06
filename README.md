# OpenMTR.github.io

# 1. Initial Project Requirements
- Expose the interface to OpenMTR as a Web API
- Deploy the API to Microsoft Azure
- Create web-based documentation for the API
  - URL paths for the exposed functionality
  - Inputs and outputs for each method
  - Sample code for Java, C#, Python, and JavaScript
- Create web page at the API root that provides a summary and functionality to upload a photo and display results of the API call.
- Log all calls to the API in SQL Server database on Azure.

## Benefits
- No security issues on internal systems involved so students can work independently
- Mature the API around our computer vision library
- Learn about deploying micro services to Azure, this will benefit both KUB and the students 

#  2. Listed Technologies
    - Semantic CSS
    - Javascript
    - Jax-RS
    - Swagger (API documentation)
    - Github (Source control / CI / CD)
    - Azure Devops
    - Azure Cloud
    - Sonar Cloud (SCA)
    - Open Liberty (IBM Webserver)
    - Ubuntu
    - Maven
    - Docker

**_ Technologies are subject to change at any time _**


# 3. Set-up 
    - Create Git repository with a README and webpage branch
    - become familiar with github interface (Fetch, Pull, Approve, etc.)
    - Use 200 OK web server extension for chrome (front-end design)
    - Set up a general container with Jax-RS and Maven
 


# 4. Workbook Entries
## James Willhoite - Jan 16
- Installed Open Liberty on local machine
- Researching Jax-RS and how Maven compiles while installing test appication to Open Liberty
### Issue 
-  *Maven wouldn't compile, research was done on the web.xml file, which resulted in finding an unneeded dependancy in "Jersey". Once it was removed all went well.

**_137 minutes_**


## Jenny Franklin Jan 16
- Updated this workbook with about notes on the set-up meeting

**_35 minutes_**


## James Willhoite - Jan 17
- Added more content to gitignore to ignore a lot of unneeded files that intelliJ will add, also Mac file

**_10 minutes_**


## James Willhoite Jan 17
- Succeeded in showing the index.html file with open-liberty, but received an error when trying to get the API to respond. 
### Issue
Exeption thrown by appication class 'com.ibm.ws.jaxrs20.server.LibertyJaxRsServerFactoryBean.doInit:294'

**_73 minutes_**


## Jenny Franklin Jan 17
- Reading about Semantic UI on their site (https://semantic-ui.com)
-	Installed Semantic via Node.js as per site instructions
 - Attempted to get navbar started using Atom
- I’m probably just moving too fast, but I’m having some trouble understanding how to call the script. I copy/pasted it into the    header as per the site instructions, but testing it is not working for whatever reason. As soon as I do, however, I’ll save it and push up to Github.

**_100 minutes_**

## Matthew Thomas Jan 17
- Finding resources to read about azure pipelines. Azure account set up prior to the start of this log. 

**_60 minutes_**

## Matthew Thomas Jan 18
- Initial setup of Pipeline infrastructure, following guide here:  https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started-yaml?view=vsts
- Pipeline was created, it created a pull request to add the yml file to the master repository

**_90 minutes_**


## Jenny Franklin Jan 18th 
- Figured out how to link Semantic to my <head> tag. 
- Got a basic first draft navbar built, including:
- Left/Right Split
- Icon with Tooltip
- Dropdown
- It took me a while to get it up and running, since I was using the link they had on the “Getting Started” page. I ended up watching
a youtube video that led me to their cdn links, and I just took the one that I needed, and cut the jQuery part
they had also added in the “Getting Started” section.
- I am only linking it in the <head> section for now, instead of using the download, for simplicity. I plan on switching to
referencing the download so that I can edit colors and such after I get the basics laid out. 

**_125 minutes_**

## James Willhoite Jan 20
- Worked off and on for the past couple of days. Have had a real hard time getting the Jax-rs set up. I know have it done and been playing around with it thanks to Matt from KUB. A lot of the tutorials out there are for GlassFish and Tomcat Application servers. These use Jesery Servlets to help contain them, Open Liberty does this for you. Once I removed those dependencies everything started to work. 
### Need to code
 - Error Class
 - Class to handle any errors and return back a response
 - Database Class
 - KUB wants a database that logs who and what was requested
 - Download file from URL
 - Next meeting we need to come up with a list of things the API will need to do (some examples above)

**_~360 minutes_**

## Matt Thomas Jan 21
- Studying and implementing CI and better code hub, getting azure webapp ready
- Having issues understanding where openliberty will be, made a webapp like Dewayne said, but it doesn’t appear it needs any OS or linux - distro behind it. As of Jan 2019 some things in azure changed, so maybe this is one?

     ### Connecting Devops organization made before (mthomas30327, project: openmtr)
      Guide: https://docs.microsoft.com/en-us/azure/app-service/web-sites-configure

 - I was doing it wrong before, so now I’ll start over with a webapp using a docker image as the environment. I’m currently configuring   a docker repo for training on a linux machine:

 - After researching Docker and custom docker builds, I’ve made a simple docker file to test with the following image, using reference
 from this: https://docs.docker.com/samples/library/open-liberty/

 - I’m not able to get the Dockerfile configuration right at the moment, I’ll try again later.

**_195 min_**

## Matt Thomas Jan 22
- Explored more docker, and ran into this problem:  
  -It looks like open-liberty doesn’t play well with Azure, will update when a solid answer is received. 

       Another Docker Guide to learn basics: https://rominirani.com/docker-tutorial-series-writing-a-dockerfile-ce5746617cd

**_60 min_**


## Jenny Franklin Jan 22 
- Dug into Semantic a little more
  - Created Footer 
  - Created placeholder logos
  - Created placeholder hero image
- Semantic doesn’t appear to have a built in hero-image feature, so I’m waiting until I get the css files to edit, and I found a code     snippet on codepen that shows how to do it manually. (180 minutes - which is incredibly pleasing number)


# JAN 23 IN-CLASS MEETING
- Discussed each week’s task with each other, explained what we had been doing 
- Discussed issues we have had:
 - Matt trying to build docker file based off an openliberty docker hub image, and the build kept being unsuccessful. Using openliberty   docker file on azure returned a message that the OS was not supported.

## Jenny Franklin Jan 23 
- Added feature boxes
- Made and Added placehold Feature .pngs using Affinty (like Photoshop)
- Added a button in navbar to report bugs
- I can do in-line color styling for grid rows, but not grid columns in rows, which is weird, but I used their default colors for now. 
 ### Problem:
    I really want the site to be responsive, but Semantic has no built-in features for menu collapse. There will have to be some javascript + custom css etc to make it happen. But we’ll see.	

**_114 minutes_**

## James Willhoite Jan 23
- Went through and set up the main API. You can issue the url http://localhost:9080/openmtr-api/api/getURL/?url=https://cdn.journaldev.com/wp-content/uploads/2012/12/java-delete-file-directory.png
And it will download the image and save it in the web directory. 
- Create a class to return the data and errors back in a JSON string
### Problem:
    Tried to test the downloaded image against Matt C library but I could not get it to import into the application. 

**_227 Minutes_**

## Matt Thomas Jan 23 
 - Started transposing this document to markup, didn’t get very far. 

**_15-20 minutes_**

## James Willhoite Jan 24
- Installed Eclipse IDE
- Went through Azure tutorial got the Hello Azure Set up
- Pulled over Jenny’s index page and pushed to Azure Webapp
- Set up new Repo
  -Pushed initial files to new repo
### Problem 
    Tried testing out my java files but could not get the api to work 
    Might need to install tomcat on local computer since azure uses tomcat container

**_180 minutes_**

## James Willhoite Jan 25 
- Installed Tomcat on localhost
- Converted from IBM Websphere to Jersey
- I converted because as I were googling for examples of applications pushed to Azure, most were using Jersey
- Got API from original Repo to work on new Repo but only in Open Liberty
### Problems 
    Cannot get Tomcat to show API. There is an error : javax.servlet.ServletException: Servlet execution threw an exception
	org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:52)

**_180 Minutes_**

## Matt Thomas Jan 26
- Did Java web-app on azure tutorial. 
- Starting pipeline for new test repository
- Waiting for weekly meeting to continue with pipeline

**_60 min_**

## James Willhoite Jan 27
- Went through a different tutorial that used Jax-RS, Maven, and a Tomcat Server
- Found out my original file structure was incorrect. I applied this same file structure to my own and was able to get it to run my API both from my local computer and Azure
-https://www.javahelps.com/2015/08/jersey-2x-hello-world.html was the tutorial I followed

**_195 minutes_**

## James Willhoite Jan 28 
- Was able to get Matt C’s OpenMeter.jar file imported into Eclipse and also into Maven.
- Maven import was a little difficult. Was able to figure it out though. Needed to have Maven install via the command line

      mvn install::install-file -Dfile=Library/openmeter.jar -DgroupId=com.mattclinard -DartifactId=openmeter -Dversion=1.0 -Dpackaging=jar -DgeneratePom=true

- Then went into the pom.xml file and added a dependency for his library

      <dependency>
			 <groupId>com.mattclinard</groupId>
			 <artifactId>openmeter</artifactId>
			 <version>1.0</version>
		 </dependency>

- after that I could add the import com.mattclinard.openmeter.* line in the Java File
### Problem
    The image is being downloaded but I am getting an error 
    org.glassfish.jersey.message.internal.WriterInterceptorExecutor$TerminalWriterInterceptor.aroundWriteTo MessageBodyWriter not found for media type=application/json, 
    In the log file

**_75 minutes_** 

## James Willhoite Jan 30
- Figured out the error I was getting 

      org.glassfish.jersey.message.internal.WriterInterceptorExecutor$TerminalWriterInterceptor.aroundWriteTo MessageBodyWriter not found for media type=application/json,

- Was due to my ReturnResponse class. I didn’t have anything for a success. It didn’t know what to return. I created a success function that returns a response.
- The getURL portion is complete. Was able to get it to download a file and test it against Matt C’s library and got a successful response. Need to code the POST function to upload the file from the form.

**_60 minutes_**

## Jenny Franklin Jan 30 
- Made document detailing project specs and schedule
- Uploaded it to Slack as pdf 
- It’s really nice - I’m very happy with it as something to include in our final project workbook. I’m sure it will change as time goes on, but I’m pleased. It did take me over two hours, which I wasn’t expecting. 

**_125 minutes_**

## Matt thomas Jan 30 
- Worked with Keith Clinard and DeWayne on creating a YAML file for the pipeline, we use a Maven generated pipeline in Azure Devops to get the initial build pipeline set up. 
- Build pipelines build the project from Master in github, then pass the files to the release pipeline, which will then distribute them (I believe just a WAR file) to the Azure infrastructure. This process begins when a pull request is merged with master in the OpenMtr-api file
- Worked with Azure Variables to determine where the WAR file was supposed to be, and discovered the use of steps in the pipeline to complete different tasks in the infrastructure.

**_90 Min_**

## James Willhoite  Feb 1
- Deleted and removed old file structure and created new file structure per Matt Clinard’s request/instructions. Pull Request created.
- Got API back up and running and is returning a 200 ok response
- Next steps are to include my old API into the new file structure 
- Took longer to configure new Pom.xml and web.xml files to get tomcat to work and recognize the Jax-Rs annotations.

**_230 Minutes_**

# Feb 2 Saturday morning meeting - all!
- Reviewed week with each other, created to-do list for Wednesday.

## Feb 2 Matt Thomas 
- Researching gitignore files and what should be excluded from a eclipse build

      Matt Clinard recommended this link to learn how to close github issues: https://github.blog/2013-05-14-closing-issues-via-pull-requests/
- It appears that James recreated the gitignore when re-creating the repo (See Jan 17)
- Updated trello with my current tasks
- Furthering CI/CD pipelines
- Due to an issue in the “copy files” task of the yaml that said 

      “ contents: '/**/*'” on line 38 (currently)

- The build never copied any files to the release pipeline. 
- By reversing the contents to say :

      \**\*

 - the build worked successfully. Now to fix the release.

**_130 mins_**

## Jenny Franklin Feb 2
- Created basic form on a new page - demo.html - for James to play with and test out the API responses

**_65 minutes_**

## James Willhoite Feb 2
- Created the API to POST a file and have it uploaded and checked Against the OpenMeter Library. 
- No testing done but went through and coded each piece as I believe they will need to be
- Took a bit to do as it required a lot of research in taking a file and being able to save it to disk. Since the file structure changed, had to figure out the new real path to be able to save the file.

**_180 Minutes_**

## Jenny Franklin Feb 3
- Resolved conflicts with the commit from Feb 2nd
- Went back and reformatted the demo form and recommited
- Added responsive expanded feature highlight segments on the homepage
- Began working on responsive features for the navbar

      I’m really frustrated here, because Semantic has a “theme” section where it gives you examples of different pages. One of them features a responsive menu. I went and copied all the jquery and edited the navbar to match exactly what it was doing, but it didn’t change anything. I finally checked by copy and pasting the example code in its entirety into a new HTML doc, and when I opened it in Chrome, it didn’t even work remotely. I made sure to copy all the dependencies and script links, etc. Nothing. 

- Added a little color and format to the highlights/selling points
- I’m definitely not happy with these in terms of final look, but I wanted to start making it look a little more formal.

**_215 minutes_**

## James Willhoite Feb 3
- Tested the API to upload the file. The tests were done via Postman. Tests were successful once I figured out how to use Postman to POST a file. 
- Had to modify a few lines of code, mainly a mistype in the Jax-rs Annotation for @FormDataParam (had it just as @FormParam, took about an hour to figure that one out).
### Problem

    Not so much as a problem but trying to figure out why I get a NullPointerException when testing for a Null or blank File post. I have the two fields in a try catch block to catch the NullPointerException, but it still throw it. Will revisit again later

**_120 minutes_**

- Added javascript to the Demo Page to allow testing. Both uploading a file and entering a url will work

**_105 Minutes_**

## Matt Thomas Feb 4 
- Read more on Markup and Jekyll
- Did more Pipeline troubleshooting, changing variables and investigating the paths Azure uses. I’m not making a ton of progress, but I’m starting to see how it comes together a little more
- Spending time reading over pull requests and getting that workflow figured out.

**_90 min_**

## Matt Thomas Feb 5 
- Deleted fork of openmtr to retry the pipeline. Currently my pipeline fork was outdated. 
- Upon recreating and configuring, ran into an error with a missing jar file. The build pipeline was unable to finish because of Matt Clinards jar file being missing from the repo. 
- After some investigation, the jar file wouldn’t load into the repo because the gitignore has *.jar in it, so a pr was made to remove that, which was quickly accepted, and the jar will be added with another PR, allowing the pipeline work to continue.
- Created a mysql database to start a Java database class for James

**_180 min_**

## Matt Thomas Feb 6
- Got a solid start on formatting some markdown for the github page.
- transcribed workbook up until this entry 





