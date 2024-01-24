pipeline {
    agent any

    environment{
        SCANNER_HOME = tool 'sonar-scanner'
    }
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'latest', url: 'https://github.com/devops-maestro17/10-Tier-MicroService-Appliction.git'
            }
        }
        stage('Static Code Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=10-Tier -Dsonar.projectName=10-Tier -Dsonar.java.binaries=. '''
                }
            }
        }
        
        stage('Building adservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/adservice') {
                            sh 'docker build -t satyasaladi9/adservice:latest .'
                            sh 'docker push satyasaladi9/adservice:latest'
                            sh 'docker rmi satyasaladi9/adservice:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building cartservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/cartservice/src/') {
                            sh 'docker build -t satyasaladi9/cartservice:latest .'
                            sh 'docker push satyasaladi9/cartservice:latest'
                            sh 'docker rmi satyasaladi9/cartservice:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building checkoutservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/checkoutservice') {
                            sh 'docker build -t satyasaladi9/checkoutservice:latest .'
                            sh 'docker push satyasaladi9/checkoutservice:latest'
                            sh 'docker rmi satyasaladi9/checkoutservice:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building currencyservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/currencyservice') {
                            sh 'docker build -t satyasaladi9/currencyservice:latest .'
                            sh 'docker push satyasaladi9/currencyservice:latest'
                            sh 'docker rmi satyasaladi9/currencyservice:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building emailservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/emailservice') {
                            sh 'docker build -t satyasaladi9/emailservice:latest .'
                            sh 'docker push satyasaladi9/emailservice:latest'
                            sh 'docker rmi satyasaladi9/emailservice:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building frontend') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/frontend') {
                            sh 'docker build -t satyasaladi9/frontend:latest .'
                            sh 'docker push satyasaladi9/frontend:latest'
                            sh 'docker rmi satyasaladi9/frontend:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building loadgenerator') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/loadgenerator') {
                            sh 'docker build -t satyasaladi9/loadgenerator:latest .'
                            sh 'docker push satyasaladi9/loadgenerator:latest'
                            sh 'docker rmi satyasaladi9/loadgenerator:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building paymentservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/paymentservice') {
                            sh 'docker build -t satyasaladi9/paymentservice:latest .'
                            sh 'docker push satyasaladi9/paymentservice:latest'
                            sh 'docker rmi satyasaladi9/paymentservice:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building productcatalogservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/productcatalogservice') {
                            sh 'docker build -t satyasaladi9/productcatalogservice:latest .'
                            sh 'docker push satyasaladi9/productcatalogservice:latest'
                            sh 'docker rmi satyasaladi9/productcatalogservice:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building recommendationservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/recommendationservice') {
                            sh 'docker build -t satyasaladi9/recommendationservice:latest .'
                            sh 'docker push satyasaladi9/recommendationservice:latest'
                            sh 'docker rmi satyasaladi9/recommendationservice:latest'
                        }
                    }
                }
            }
        }
        
        stage('Building shippingservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/shippingservice') {
                            sh 'docker build -t satyasaladi9/shippingservice:latest .'
                            sh 'docker push satyasaladi9/shippingservice:latest'
                            sh 'docker rmi satyasaladi9/shippingservice:latest'
                        }
                    }
                }
            }
        }
        
        stage('Deploy app to K8s') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'cluster-name', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://656F31A670655D13C9BBA898F3BA9597.gr7.ap-south-1.eks.amazonaws.com') {
                    sh 'kubectl apply -f deployment-service.yml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
                }
            }
        }
        
    }
}
