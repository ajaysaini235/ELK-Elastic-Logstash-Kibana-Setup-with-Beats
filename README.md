
                 *****************************************************
                                  
**************  ELK (Elasticsearch Logstash Kibana) Instolation setup with Beats or Filebeat ***********

                                Only For Linux or Mac 

                 ******************************************************
  
       
    =============
    Java          ===>>> 
    =============  

              
		  >>  sudo add-apt-repository ppa:webupd8team/java
		  >>  sudo apt-get update
		  >>  sudo apt-get install oracle-java7-set-default
   



    =============
    Brew         ===>>> 
    =============
                 

                  1. install brew  
              
                     /***  Note : Help from ( http://brew.sh/ ) .Homebrew installs packages ***/

                      >> apt-get install build-essential curl git m4 ruby texinfo libbz2-dev libcurl4-openssl-dev 
                         libexpat-dev libncurses-dev zlib1g-dev 
                        
                      >>  ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/linuxbrew/go/install)"
 
                      >>  sudo gedit .bashrc 

                 2.   Press enter then past below three command in .bashrc file and after save this file restart your system.
      
                      >>  export PATH="$HOME/.linuxbrew/bin:$PATH"
                      >>  export MANPATH="$HOME/.linuxbrew/share/man:$MANPATH"
                      >>  export INFOPATH="$HOME/.linuxbrew/share/info:$INFOPATH"



                         /***  Note : Common Issues during installs packages  by brew command ***/
                         
                         *************************************************************************

                         Issue : cannot load such file -- language/node
                         
                         Solution : Run following command on your terminal.
                              >> brew update
                              >> brew doctor

                         **************************************************************************

    =============
    Elasticsearch ===>>> 
    =============
                 
  
                 1. install elasticsearch 

                      >>  brew install elasticsearch

                 2. install plugin in elasticsearch

                        1. Find plugin file in  ~/.linuxbrew/Cellar/elasticsearch/ and copy path.
                        
                        2. like this  >>  ~/.linuxbrew/Cellar/elasticsearch/2.3.5/libexec/bin/plugin and change your version 

                        3. then exit form bin by  /*  cd ..  */  

                        4. run command bin/plugin install plugin_name
                              
                            example : 
                            1. ubuntu@ubuntu-1:~/.linuxbrew/Cellar/elasticsearch/2.3.5/libexec$ bin/plugin install royrusso/elasticsearch-HQ  
                
                  3. Now elasticsearch install in your system . for run elasticsearch

                       1. cd ~/
                       2. elasticsearch

                  /***    Note: Default run on localhost:9200/   ***/
                               



    =============
    Logstash     ===>>> 
    =============
                 

                 1. install elasticsearch 

                       >> brew install logstash

                 2. install plugin in logstash

                        1. Find plugin file in  ~/.linuxbrew/Cellar/elasticsearch/ and copy path.
                        
                        2. like this  >>  ~/.linuxbrew/Cellar/elasticsearch/2.3.5/libexec/bin/plugin and change your version 

                        3. then exit form bin by  /*  cd ..  */  

                        4. run command bin/plugin install plugin_name
                              
                            example : 
                             1. ubuntu@ubuntu-1:~/.linuxbrew/Cellar/elasticsearch/2.3.5/libexec$ bin/plugin install logstash-input-beats  
                
                  3. Now elasticsearch install in your system . for run elasticsearch

                       1. cd ~/
                       2. logstash -f  < configuration file path >

    

    =============
    Filebeat     ===>>> 
    =============  
                   
		   Install  =>> curl -L -O https://download.elastic.co/beats/filebeat/filebeat_1.3.0_amd64.deb
	    			sudo dpkg -i filebeat_1.3.0_amd64.deb   

                   Configuration  ==>> change configuration as your requirement in file  at /**   /etc/filebeat/filebeat.yml   **/

                   Edit Configuration ==>> sudo gedit /etc/filebeat/filebeat.yml

                   Start ==>> sudo /etc/init.d/filebeat start 

                   Stop ==>> sudo /etc/init.d/filebeat stop

                   Restart ==>> sudo /etc/init.d/filebeat restart
  
                   Status ==>> sudo /etc/init.d/filebeat status    

     
    =============
    Kibana     ===>>> 
    =============  
                   
	           /***   Note : Go to this link download and run kibana  >>>  https://www.elastic.co/guide/en/kibana/4.1/setup.html  **/
     

    =============
    Shield     ===>>> 
    =============  
                   
	        Step 1: Install Shield
			    bin/plugin install elasticsearch/license/latest
			    bin/plugin install elasticsearch/shield/latest

			Step 2: Start Elasticsearch
			    bin/elasticsearch

			Step 3: Add an admin user
			   bin/shield/esusers useradd es_admin -r admin

			Step 4: Try it with a user
		           curl -u es_admin -XGET 'http://localhost:9200/'

  
