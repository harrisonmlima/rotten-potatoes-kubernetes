pipeline 
{
    agent any
    stages 
    {
        stage ( 'Build Docker Image')
        {
            steps
            {
                script
                {
                    dockerapp = docker.build("harrisonlima/rotten-potatoes:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                }
            }
        }

        stage ('Push Docker Image')
        {
            steps
            {
                script
                {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                    {
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }

        stage ('Deploy Kubernetes')
        {
            environment
            {
                tag_version = "${env.BUILD_ID}"
            }
            steps
            {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'jenkins',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                        sh 'sed -i "s/{{TAG}}/$tag_version/g" ./src/k8s/api/deployment.yaml'
                        sh 'kubectl apply -f ./src/k8s -R'
                        
                    }
                    
            }
        }
    }
}