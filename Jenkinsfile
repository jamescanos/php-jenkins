pipeline {
    agent none
    
    stages {
        stage('Clonar código') {
            agent any
            steps {
                git branch: 'main', 
                    url: 'https://github.com/jamescanos/php-jenkins.git'
                echo 'Código PHP clonado'
            }
        }
        
        stage('Validar PHP') {
            agent {
                docker {
                    image 'php:8.2-cli'  # Contenedor con PHP instalado
                    reuseNode true
                }
            }
            steps {
                sh 'php -l index.php'
                echo 'Sintaxis PHP validada'
            }
        }
        
        stage('Ejecutar tests') {
            agent {
                docker {
                    image 'php:8.2-cli'  # Usamos el mismo contenedor
                    reuseNode true
                }
            }
            steps {
                sh 'php -r "echo \"Tests simulados exitosos\n\";"'
                echo 'Tests ejecutados'
            }
        }
        
        stage('Desplegar') {
            agent any
            steps {
                echo 'Aplicación PHP lista para desplegar'
                echo 'Puedes agregar aquí tus comandos de despliegue'
            }
        }
    }
    
    post {
        success {
            echo '¡Pipeline ejecutado con éxito!'
        }
        failure {
            echo 'Pipeline falló. Revisar los logs.'
        }
    }
}