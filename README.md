# Jenkins Server 

  => install java and maven
   
    apt update && apt install openjdk-21-jdk -y && apt install maven -y 

  or
   
    sudo apt update
    sudo apt install fontconfig openjdk-21-jre
    java -version


   => install jenkins

   sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
   https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
    echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null
    sudo apt update
    sudo apt install jenkins

----------------------------------------------------------------------------------------------------------------
