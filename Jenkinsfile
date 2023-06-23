pipeline {
	agent {
		label {
			label "built-in"
			customWorkspace "/mnt/practical"
		}
	}
	
	environment {
						
				composeurl = "https://github.com/santosh1194/compose-file.git"
				warurl = "https://tomcat.apache.org/tomcat-7.0-doc/appdev/sample/sample.war"
				indexurl ="https://github.com/santosh1194/index-file.git"
		}

	stages {
		
		stage ("parallel stages") {

            parallel {
						
				stage ("dev-deployment") {
					agent {
							label {
								label "dev"
								customWorkspace "/mnt/project/"
							}
					}
				
					steps {
						dir ("/mnt/"){
								sh "rm -rf /mnt/compose-dir/*"
								sh "git clone ${composeurl}"
								sh "chmod -R 777 /mnt/compose-dir/compose-file/docker-compose.yml"
						}
						dir ("/mnt/wars"){
								sh "rm -rf /mnt/wars/*"
								sh "wget ${warurl}"
								sh "chmod -R 777 /mnt/wars/sample.war"
						}
						dir ("/mnt/webpage"){
								sh "rm -rf /mnt/webpage/*"
								sh "git clone ${indexurl}"
								sh "chmod -R 777 /mnt/webpage/index-file/index.html"
						}
					
					sh "cd /mnt/compose-dir/ && sudo docker-compose up -d"
					
					}
				}
				
				
				stage ("qa-deployment") {
					agent {
							label {
								label "qa"
								customWorkspace "/mnt/project/"
							}
					}
				
					steps {
						dir ("/mnt/"){
								sh "rm -rf /mnt/compose-dir/*"
								sh "git clone ${composeurl}"
								sh "chmod -R 777 /mnt/compose-dir/compose-file/docker-compose.yml"
						}
						dir ("/mnt/wars"){
								sh "rm -rf /mnt/wars/*"
								sh "wget ${warurl}"
								sh "chmod -R 777 /mnt/wars/sample.war"
						}
						dir ("/mnt/webpage"){
								sh "rm -rf /mnt/webpage/*"
								sh "git clone ${indexurl}"
								sh "chmod -R 777 /mnt/webpage/index-file/index.html"
						}
					
					sh "cd /mnt/compose-dir/ && sudo docker-compose up -d"
					}
				}
			}
			
		}
	}
}
