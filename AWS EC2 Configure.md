# Configure EC2 on AWS

1. Create and Log into AWS Console  

2. Create & access to EC2 instance (use free tier)  
&nbsp;&nbsp;Note :&nbsp;Add Security Groups - &nbsp;3838 - Shiny Server  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;8787 - R Studio  
&nbsp;&nbsp;&nbsp;&nbsp;Add Key pair for SSH access  
&nbsp;&nbsp;&nbsp;&nbsp;Access Instance by using SSH key .pem file  

3. Configure Instance  
&nbsp;&nbsp;Note :&nbsp;Update system  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo apt-get update`  
&nbsp;&nbsp;&nbsp;&nbsp;Upgrade System  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo apt-get upgrade`  
                    
4. Configure R and Shiny on the instance  
&nbsp;&nbsp;Note :&nbsp;Install r-base and r-base-dev  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo apt-get install r-base`  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo apt-get install r-base-dev`  
&nbsp;&nbsp;&nbsp;&nbsp;Install required r packages  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo su — -c “R -e \”install.packages(‘shiny’, repos = ‘http://cran.rstudio.com/')\""`  
&nbsp;&nbsp;&nbsp;&nbsp;* change 'shiny' according to your package name  
&nbsp;&nbsp;&nbsp;&nbsp;Install shiny server  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo apt-get install gdebi-core`  
&nbsp;&nbsp;&nbsp;&nbsp;`wget https://download3.rstudio.org/ubuntu-14.04/x86_64/shiny-server-1.5.7.907-amd64.deb`  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo gdebi shiny-server-1.5.7.907-amd64.deb`  
&nbsp;&nbsp;&nbsp;&nbsp;Install R Studio Server  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo apt-get install gdebi-core`  
&nbsp;&nbsp;&nbsp;&nbsp;`wget https://download2.rstudio.org/rstudio-server-1.1.456-amd64.deb`  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo gdebi rstudio-server-1.1.456-amd64.deb`  

5. Configure user access  
&nbsp;&nbsp;Note :&nbsp;Add new user  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo adduser username`  
&nbsp;&nbsp;&nbsp;&nbsp;Enable sudo in sudoers for that user  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo nano /etc/suroers`  
&nbsp;&nbsp;&nbsp;&nbsp;Add Follwing Line  
&nbsp;&nbsp;&nbsp;&nbsp;`%username ALL=(ALL:ALL) ALL`  
&nbsp;&nbsp;&nbsp;&nbsp;Check sudoers  
&nbsp;&nbsp;&nbsp;&nbsp;`cat /etc/sudoers`  

6. Log into R studo server and design apps  
&nbsp;&nbsp;Note :&nbsp;Deploy app to shiny server  
&nbsp;&nbsp;&nbsp;&nbsp;`sudo cp -r dir* /srv/shiny-server`  

7. Also you can use pre-implemented apps on shiny-server  
&nbsp;&nbsp;Note :&nbsp;Coppy from git  
&nbsp;&nbsp;&nbsp;&nbsp;`cd /srv/shiny-server`  
&nbsp;&nbsp;&nbsp;&nbsp;`git clone git-url`  
