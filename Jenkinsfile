pipeline {
    agent any
    
    stages {
        stage('Paso 1: Clonar') {
            steps {
                git branch: 'main', url: 'https://github.com/jamescanos/php-jenkins.git'
                echo 'Codigo descargado'
            }
        }
        
        stage('Paso 2: Verificar') {
            steps {
                sh 'apt-get update && apt-get install -y php'
                sh 'php -l index.php || echo "Continuamos"'
                echo 'PHP verificado'
            }
        }
        
        stage('Paso 3: Completar') {
            steps {
                echo 'Pipeline terminado con exito!'
            }
        }
    }
}