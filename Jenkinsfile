pipeline {
		agent {
		node {
		label ('built-in')
		
		}
		}

		stages {
			stage ('22Q1-deploy'){
			steps {
			dir ('/mnt/repos') {
				sh "rm -rf *"
				sh "git clone https://github.com/ronitunale/dockerassi.git -b 22Q1 "
				sh "chmod -R 777 /mnt"
				sh "yum install docker -y"
				sh "systemctl start docker"
				sh "docker system prune -a -f"
				sh "docker pull httpd"
				sh "docker run -itdp 80:80 --name 22Q1 httpd"
				sh "docker cp /mnt/repos/22Q1/index.html 22Q1:/usr/local/apache2/htdocs"
				
				}
				}
				}
				
				stage ('22Q2-deploy'){
			steps {
			dir ('/mnt/repos') {
				sh "git clone https://github.com/ronitunale/dockerassi.git -b 22Q2"
				sh "docker run -itdp 90:80 --name 22Q2 httpd"
				sh "docker cp /mnt/repos/22Q2/index.html 22Q2:/usr/local/apache2/htdocs"
				
				}
				}
				}

				stage ('22Q3-deploy'){
			steps {
			dir ('/mnt/repos') {
				sh "git clone https://github.com/ronitunale/dockerassi.git -b 22Q1 "
				sh "docker run -itdp 8080:80 --name 22Q3 httpd"
				sh "docker cp /mnt/repos/22Q3/index.html 22Q3:/usr/local/apache2/htdocs"
				
				}
				}
				}

	
	}
}
