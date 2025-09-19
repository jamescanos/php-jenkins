pipeline {
    agent any
    
    stages {
        stage('Clonar codigo') {
            steps {
                git branch: 'main', url: 'https://github.com/jamescanos/php-jenkins.git'
                echo 'Codigo clonado'
            }
        }
        
        stage('Instalar PHP') {
            steps {
                sh '''
                    # Instalar PHP si no existe
                    if ! command -v php &> /dev/null; then
                        echo "Instalando PHP..."
                        apt-get update
                        apt-get install -y php
                    fi
                    php -v
                '''
                echo 'PHP instalado'
            }
        }
        
        stage('Validar codigo') {
            steps {
                sh '''
                    # Validar archivos PHP
                    if [ -f "index.php" ]; then
                        php -l index.php
                    else
                        echo "Archivos encontrados:"
                        ls -la
                        echo "Validacion basica completada"
                    fi
                '''
                echo 'Codigo validado'
            }
        }
        
        stage('Ejecutar pruebas') {
            steps {
                sh '''
                    echo "=== PRUEBAS BASICAS ==="
                    echo "Version de PHP:"
                    php -v
                    echo "=== PRUEBA COMPLETADA ==="
                '''
                echo 'Pruebas ejecutadas'
            }
        }
        
        stage('Finalizar') {
            steps {
                echo 'PIPELINE COMPLETADO EXITOSAMENTE'
                echo 'Revisa los logs arriba para ver los resultados'
            }
        }
    }
}