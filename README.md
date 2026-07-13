# Jenkins Server 

  Install java and maven
  
    apt update && apt install openjdk-21-jdk -y && apt install maven -y 

  Install only Java ( 21 or + version )
   
    sudo apt update
    sudo apt install fontconfig openjdk-21-jre
    java -version


   install jenkins 


      sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
      https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
      echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
      https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
      /etc/apt/sources.list.d/jenkins.list > /dev/null
      sudo apt update
       sudo apt install jenkins
       
----------------------------------------------------------------------------------------------------------------

# Sonar Server Setup

Install and configure Database

(Install java and PostgreSQL )

     apt update && apt install openjdk-17-jdk -y && apt install postgresql -y && systemctl start postgresql
     
( Login to PostgreSQL )

    sudo -u postgres psql

>> create User 

    CREATE USER linux PASSWORD 'redhat';


>> create Database 

    CREATE DATABASE sonarqube;
    
>> grant previleges of DB to user  

    GRANT ALL PRIVILEGES ON DATABASE sonarqube TO linux;

>> start connection with database  

    \c sonarqube;

>> Grant all previleges to user   

    GRANT ALL PRIVILEGES ON SCHEMA public TO linux;

>> Quit the PostgreSQL

    \q

 # Configure Linux Machine

   
     sysctl -w vm.max_map_count=524288 && \
     sysctl -w fs.file-max=131072 && \ 
     ulimit -n 131072 && \
     ulimit -u 8192

# Install and Configure Sonarqube

( Install SonarQube Software )
      
      wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-25.5.0.107428.zip
      
( Install unzip command package )

    apt install unzip -y

( Unzip the installed software )

    unzip sonarqube-25.5.0.107428.zip

( Move the sonarqube package to /opt directory change directory to /opt  ) 

    mv sonarqube-25.5.0.107428 /opt/sonar & \
    cd /opt/sonar

Edit Sonar properties 

- in Database section 
>> sonar.jdbc.username=linux     ( username of DB  )
>> sonar.jdbc.password=redhat    ( password of DB )
>> sonar.jdbc.url=jdbc:postgresql://localhost/sonarqube   ( url of DB )

    vim conf/sonar.properties

Create a Sonar User (who runs the sonar server ) 

    useradd sonar -m && \
    chown sonar:sonar -R /opt/sonar  && \
    su sonar

Go to " /opt/sonar/bin/linux-x86-64 " to execute the sonar script file to start the server by the user ( Sonar User only)

    cd /opt/sonar/bin/linux-x86-64  && \
    ./sonar.sh start  && \
    ./sonar.sh status

----------------------------------------------------------------------------------------------------------------------------------------------------------------
