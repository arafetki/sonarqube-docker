## SONARQUBE SERVER WITH POSTGRESQL DATABASE


#### To run the containers in detached mode :
    docker-compose up -d
    
##### Access web ui on http://localhost:9000
##### Login : admin Password : admin

### DEBUG :

- #####  Check logs of sonarqube server service

    docker-compose logs -f server

- #####  Check logs of sonarqube db service

    docker-compose logs -f db
    
### COMMON ERROR IF YOU ARE USING LINUX :
bootstrap check failure [1] of [1]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]

-  Locate the configuration file where kernel parameters are set. On most Linux systems, this file is /etc/sysctl.conf

- Add the following line to the configuration file to set vm.max_map_count to the minimal required value (262144) vm.max_map_count=262144

        sudo echo "vm.max_map_count=262144" >> /etc/sysctl.conf


- Apply the Changes

        sudo sysctl -p
        

- Restart your SonarQube and PostgreSQL containers:

        docker-compose down

### COMMON ERROR IF YOU ARE USING WINDOWS :

bootstrap check failure [1] of [1]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]

### SOLLUTION:
1- Open PowerShell
2- Apply these two commands : 
        1) wsl -d docker-desktop
        2) sysctl -w vm.max_map_count=262144
3- Run Again docker-compose up -d 
        docker-compose up -d
