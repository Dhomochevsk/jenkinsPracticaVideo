pipeline {
    agent any
    environment{
        CONTENEDOR='mi-contenedor'
        IMAGEN='mi-imagen'
    }
    stages{
        stage('Preparar Entorno Docker'){
            steps{
                script{
                    sh "docker stop ${env.CONTENEDOR} || true"
                    sh "docker rm ${env.CONTENEDOR} || true"
                }
            }
        }
        stage('Clonar Repositorio'){
            steps{
                script{
                    git ''
                }
            }
        }
        stage('Construir Imagen Docker'){
            steps{
                script{
                    sh "docker build -t ${env.IMAGEN} ."
                }
            }
        }
        stage('Desplegar en Docker'){
            steps{
                script{
                    sh "docker run -d -p 8100:80 --name ${env.CONTENEDOR} ${env.IMAGEN}"
                }
            }
        }
    }
}