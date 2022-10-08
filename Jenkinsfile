pipeline {
		agent {
		node {
		label ('172.31.32.220')
		
		}
		}

		stages {
			stage ('22Q1-deploy'){
			steps {
			dir ('/mnt/repos1') {
				sh "sudo rm -rf *"
				sh "sudo git clone https://github.com/ronitunale/dockerassi.git -b 22Q1 "
				sh "sudo chmod -R 777 /mnt"
				sh "sudo yum install docker -y"
				sh "sudo systemctl start docker"
				sh "sudo docker kill 22Q1"
				sh "sudo docker system prune -a -f"
				sh "sudo docker pull httpd"
				sh "sudo docker run -itdp 80:80 --name 22Q1 httpd"
				sh "sudo docker cp /mnt/repos1/dockerassi/index.html 22Q1:/usr/local/apache2/htdocs"
				
				}
				}
				}
				
				stage ('22Q2-deploy'){
			steps {
			dir ('/mnt/repos2') {
				sh "sudo rm -rf *"
				sh "sudo git clone https://github.com/ronitunale/dockerassi.git -b 22Q2"
				sh "sudo docker run -itdp 90:80 --name 22Q2 httpd"
				sh "sudo docker cp /mnt/repos2/dockerassi/index.html 22Q2:/usr/local/apache2/htdocs"
				
				}
				}
				}

				stage ('22Q3-deploy'){
			steps {
			dir ('/mnt/repos3') {
				sh "sudo rm -rf *"
				sh "sudo git clone https://github.com/ronitunale/dockerassi.git -b 22Q3 "
				sh "sudo docker run -itdp 8181:80 --name 22Q3 httpd"
				sh "sudo docker cp /mnt/repos3/dockerassi/index.html 22Q3:/usr/local/apache2/htdocs"
				
				}
				}
				}

	
	}
}
