# Configure EC2 on AWS

1. Create and Log into AWS Console  

2. Create & access to EC2 instance (use free tier)  
&nbsp;        Note :  Add Security Groups -   3838 - Shiny Server  
                                        8787 - R Studio  
                Add Key pair for SSH access  
                Access Instance by using SSH key .pem file  

3. Configure Instance  
        Note :  Update system  
                    `sudo apt-get update`  
                Upgrade System  
                    `sudo apt-get upgrade`  
                    
4. Configure R and Shiny on the instance  
        Note :  Install r-base and r-base-dev  
                    `sudo apt-get install r-base`  
                    `sudo apt-get install r-base-dev`  
                Install required r packages  
                    `sudo su — -c “R -e \”install.packages(‘shiny’, repos = ‘http://cran.rstudio.com/')\""`  
                        * change 'shiny' according to your package name  
                Install shiny server  
                    `sudo apt-get install gdebi-core`  
                    `wget https://download3.rstudio.org/ubuntu-14.04/x86_64/shiny-server-1.5.7.907-amd64.deb`  
                    `sudo gdebi shiny-server-1.5.7.907-amd64.deb`  
                Install R Studio Server  
                    `sudo apt-get install gdebi-core`  
                    `wget https://download2.rstudio.org/rstudio-server-1.1.456-amd64.deb`  
                    `sudo gdebi rstudio-server-1.1.456-amd64.deb`  

5. Configure user access  
        Note :  Add new user  
                    `sudo adduser username`  
                Enable sudo in sudoers for that user  
                    `sudo nano /etc/suroers`  
                          Add Follwing Line  
                              `%username ALL=(ALL:ALL) ALL`  
                Check sudoers  
                    `cat /etc/sudoers`  
6. Log into R studo server and design apps  
        Note :  Deploy app to shiny server  
                    `sudo cp -r dir* /srv/shiny-server`  

7. Also you can use pre-implemented apps on shiny-server  
        Note :  Coppy from git  
                    `cd /srv/shiny-server'  
                    `git clone git-url`  
