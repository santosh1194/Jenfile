pipeline {
        agent {
                label {
                        label "built-in"
                        customWorkspace "/mnt/job/"
                }
        }

        stages {
                stage ("parallel stages") {

                        parallel {

                                stage ("slave 1") {
                                        agent {
											label {
												label "dev"
												customWorkspace "/mnt/data/"
											}
										}
										steps {
											sh "sudo rm -rf /mnt/data/*"
											sh "sudo chmod -R 777 /mnt/data"
											sh "sudo git clone -b 23Q1 https://github.com/santosh1194/practice.git"
											sh "sudo chmod -R 777 /mnt/data/practice/index.html"
											sh "sudo yum install docker -y"
											sh "sudo service docker restart"
											sh "sudo docker system prune -a -f"
											sh "sudo docker run -itdp 70:80 -v /mnt/data/practice:/usr/local/apache2/htdocs/ --name 23Q1 httpd"
										}
                                }
								
								stage ("slave 2") {
                                                    			    agent {
											label {
												label "qa"
												customWorkspace "/mnt/data/"
											}
										}
										steps {
											sh "rm -rf /mnt/data/*"
											sh "sudo chmod -R 777 /mnt/data"
                                                                                        sh "git clone -b 23Q2 https://github.com/santosh1194/practice.git"
											sh "sudo chmod -R 777 /mnt/data/practice/index.html"
											sh "sudo yum install docker -y"
											sh "sudo service docker restart"
											sh "sudo docker system prune -a -f"
											sh "sudo docker run -itdp 80:80 -v /mnt/data/practice:/usr/local/apache2/htdocs/ --name 23Q2 httpd"
										}
                                }
								
							/*	stage ("slave 3") {
                                                                            agent {
											label {
												label "uat"
												customWorkspace "/mnt/data/"
											}
										}
										steps {
											sh "rm -rf /mnt/data/*"
											sh "sudo chmod -R 777 /mnt/data"
                                                                                        sh "git clone -b 23Q3 https://github.com/santosh1194/practice.git"
											sh "sudo chmod -R 777 /mnt/data/practice/index.html"
											sh "sudo yum install docker -y"
											sh "sudo service docker restart"
											sh "sudo docker system prune -a -f"
											sh "sudo docker run -itdp 90:80 --name 23Q3 httpd"
											sh "sudo docker cp /mnt/data/practice/index.html 23Q3:/usr/local/apache2/htdocs/"
                                        }
                                }
							*/

                        								
											
						}
                }
        }
}
