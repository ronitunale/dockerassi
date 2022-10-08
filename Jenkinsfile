pipeline {
		agent {
		node {
		label ('built-in')
		
		}
		}

		stages {
			stage ('Master-deploy'){
			steps {
			dir ('/mnt/repos') {
				sh "rm -rf *"
				sh "git clone https://github.com/ronitunale/dockerassi.git "
				sh "chmod -R 777 /mnt"
				sh "yum install docker -y"
				sh "systemctl start docker"
				sh "docker system prune -a -f"
				sh "docker pull httpd"
				sh "docker run -itdp 90:80 --name ronit httpd"
				sh "docker cp /mnt/repos/dockerassi/index.html ronit:/usr/local/apache2/htdocs"
				
				}
		}
		}
		}
		}
