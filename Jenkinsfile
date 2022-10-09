pipeline {
		agent {
		node {
			label ('built-in')

		}		
		}

		stages {
			stage ('22Q1-deploy') {
				steps {
				dir ('/mnt/project/22Q1') {
					sh "yum install git -y"
					sh "chmod -R 777 /mnt"
					sh "git clone https://github.com/ronitunale/dockerassi.git -b 22Q1"
					sh "yum install docker -y"
					sh "systemctl start docker"
					sh "docker run -itdp 80:80 --name 22Q1 httpd"
					sh "docker cp /mnt/project/22Q1/dockerassi/index.html 22Q1:/usr/local/apache2/htdocs"	
		}
		}
		}
		
		stage ('22Q2-deploy') {
				steps {
				dir ('/mnt/project/22Q2') {
					sh "git clone https://github.com/ronitunale/dockerassi.git -b 22Q2"
					sh "docker run -itdp 90:80 --name 22Q2 httpd"
					sh "docker cp /mnt/project/22Q2/dockerassi/index.html 22Q2:/usr/local/apache2/htdocs"	
		}
		}
		}
		
		stage ('22Q3-deploy') {
				steps {
				dir ('/mnt/project/22Q3') {
					sh "git clone https://github.com/ronitunale/dockerassi.git -b 22Q3"
					sh "docker run -itdp 8181:80 --name 22Q3 httpd"
					sh "docker cp /mnt/project/22Q3/dockerassi/index.html 22Q3:/usr/local/apache2/htdocs"	
		}
		}
		}
			
		
		}



}
