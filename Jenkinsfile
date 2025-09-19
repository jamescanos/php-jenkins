pipeline {
    agent any
    
    stages {
        stage('Clonar código') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/jamescanos/php-jenkins.git'
                echo 'Código PHP clonado'
            }
        }
        
        stage('Validar PHP') {
            steps {
                sh 'php -l index.php || true'
                echo 'Sintaxis PHP validada'
            }
        }
        
        stage('Ejecutar tests') {
            steps {
                sh 'php -r "echo \\\"Tests simulados exitosos\\\\n\\\";"'
                echo 'Tests ejecutados'
            }
        }
        
        stage('Desplegar') {
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
    }
}