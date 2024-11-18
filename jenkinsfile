pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *') 
    }

    stages {
        stage('Obtener código') {
            steps {
                echo 'Obteniendo el código del repositorio...'
                checkout scm
            }
        }
        stage('Compilación') {
            steps {
                echo 'Compilando el código...'
                sh 'mvn clean compile'
            }
        }
        stage('Pruebas') {
            steps {
                echo 'Ejecutando pruebas...'
                sh 'mvn test'
            }
        }
        stage('Notificaciones') {
            steps {
                echo 'Enviando notificaciones...'
                mail to: 'jandresrodriguez4@poligran.edu.co',
                     subject: "Notificación: Resultado del pipeline",
                     body: "El pipeline ha finalizado. El test realizado por el subgrupo 20 ha sido un exito."
            }
        }
        stage('Despliegue') {
            steps {
                echo 'Desplegando en el entorno de pruebas....'

                

            }
        }
    }

    post {
        success {
            echo 'Pipeline completado exitosamente.'
        }
        failure {
            echo 'El pipeline falló. Verifica los logs.'
        }
    }
}