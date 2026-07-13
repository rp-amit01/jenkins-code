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

    CREATE USER linux PASSWORD 'redhat';
