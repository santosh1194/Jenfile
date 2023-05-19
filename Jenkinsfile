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
												customWorkspace "/mnt/slave1/"
											}
										}
										steps {
											sh "sudo rm -rf /mnt/slave1/*"
											sh "sudo yum install git -y"
                                            sh "sudo git clone -b 23Q1 https://github.com/santosh1194/practice.git"
											sh "sudo chmod -R 777 /mnt/slave1/practice/index.html"
											sh "sudo yum install docker -y"
											sh "sudo service docker restart"
											sh "sudo docker system prune -a -f"
											sh "sudo docker run -itdp 70:80 --name 23Q1 httpd"
											sh "sudo docker cp /mnt/slave1/practice/index.html 23Q1:/usr/local/apache2/htdocs/"
                                        }
                                }
								
								stage ("slave 2") {
                                        agent {
											label {
												label "qa"
												customWorkspace "/mnt/slave2/"
											}
										}
										steps {
											sh "rm -rf /mnt/slave2/*"
                                            sh "git clone -b 23Q2 https://github.com/santosh1194/practice.git"
											sh "sudo chmod -R 777 /mnt/slave2/practice/index.html"
											sh "sudo yum install docker -y"
											sh "sudo service docker restart"
											sh "sudo docker system prune -a -f"
											sh "sudo docker run -itdp 70:80 --name 23Q2 httpd"
											sh "sudo docker cp /mnt/slave2/practice/index.html 23Q2:/usr/local/apache2/htdocs/"
                                        }
                                }
								
								stage ("slave 3") {
                                        agent {
											label {
												label "uat"
												customWorkspace "/mnt/slave3/"
											}
										}
										steps {
											sh "rm -rf /mnt/slave3/*"
                                            sh "git clone -b 23Q3 https://github.com/santosh1194/practice.git"
											sh "sudo chmod -R 777 /mnt/slave3/practice/index.html"
											sh "sudo yum install docker -y"
											sh "sudo service docker restart"
											sh "sudo docker system prune -a -f"
											sh "sudo docker run -itdp 70:80 --name 23Q3 httpd"
											sh "sudo docker cp /mnt/slave3/practice/index.html 23Q3:/usr/local/apache2/htdocs/"
                                        }
                                }
                        								
											
												
						}
                }
        }
}
