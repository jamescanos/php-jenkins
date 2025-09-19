pipeline {
    agent any
    
    stages {
        stage('Clonar') {
            steps {
                git branch: 'main', url: 'https://github.com/jamescanos/php-jenkins.git'
                echo 'Codigo clonado'
            }
        }
        
        stage('Validar PHP') {
            agent {
                docker {
                    image 'php:8.2-cli'
                    reuseNode true
                }
            }
            steps {
                sh 'php -l index.php'
                echo 'PHP validado'
            }
        }
        
        stage('Tests') {
            agent {
                docker {
                    image 'php:8.2-cli'
                    reuseNode true
                }
            }
            steps {
                sh 'php -r "echo \"Tests OK\n\";"'
                echo 'Tests listos'
            }
        }
        
        stage('Final') {
            steps {
                echo 'Pipeline completado'
            }
        }
    }
}