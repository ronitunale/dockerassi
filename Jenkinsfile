pipeline {
		agent {
		node {
		label ('built-in')
		
		}
		}

		stages {
			stages ('Master') {
			
			stage ('Copy-repo-master') {
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
		
		stages ('parallel-execution-slave') {
		
		parallel {
				stages ('slave-1') {
				agent {
				node {
					label ('172.31.10.58')

				}
				}
			
			stage ('Copy-repo-22Q1') {
			steps {
			dir ('/mnt/repos') {
				sh "sudo rm -rf *"
				sh "sudo yum install git -y"
				sh "sudo git clone https://github.com/ronitunale/dockerassi.git -b 22Q1"
				sh "sudo chmod -R 777 /mnt"
				sh "sudo yum install docker -y"
				sh "sudo docker system prune -a -f"
				sh "sudo systemctl start docker"
				sh "sudo docker pull httpd"
				sh "sudo docker run -itdp 100:80 --name ronit httpd"
				sh "sudo docker cp /mnt/repos/22Q1/index.html ronit:/usr/local/apache2/htdocs"
				
				}
		}
		}
		}
			stages ('slave-2') {
				agent {
				node {
					label ('172.31.4.125')

				}
				}
			
			stage ('Copy-repo-22Q2') {
			steps {
			dir ('/mnt/repos') {
				sh "sudo rm -rf *"
				sh "sudo yum install git -y"
				sh "sudo git clone https://github.com/ronitunale/dockerassi.git -b 22Q2"
				sh "sudo chmod -R 777 /mnt"
				sh "sudo yum install docker -y"
				sh "sudo docker system prune -a -f"
				sh "sudo systemctl start docker"
				sh "sudo docker pull httpd"
				sh "sudo docker run -itdp 8080:80 --name ronit httpd"
				sh "sudo docker cp /mnt/repos/22Q2/index.html ronit:/usr/local/apache2/htdocs"
				
				}
		}
		}
		}
		stages ('slave-3') {
				agent {
				node {
					label ('172.31.9.129')

				}
				}
			
			stage ('Copy-repo-22Q3') {
			steps {
			dir ('/mnt/repos') {
				sh "sudo rm -rf *"
				sh "sudo yum install git -y"
				sh "sudo git clone https://github.com/ronitunale/dockerassi.git -b 22Q3"
				sh "sudo chmod -R 777 /mnt"
				sh "sudo yum install docker -y"
				sh "sudo docker system prune -a -f"
				sh "sudo systemctl start docker"
				sh "sudo docker pull httpd"
				sh "sudo docker run -itdp 8181:80 --name ronit httpd"
				sh "sudo docker cp /mnt/repos/22Q3/index.html ronit:/usr/local/apache2/htdocs"
				
				}
		}
		}
		}
		
		
		}
		}
		}
		

}
