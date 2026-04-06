pipeline {
    agent any
    stages {
        stage('Despliegue a Nginx') {
            steps {
                // Copiamos el index al directorio de Nginx
                sh 'sudo cp index.html /usr/share/nginx/html/index.html'
                echo '¡Despliegue exitoso en el servidor web!'
            }
        }
    }
}