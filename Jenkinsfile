node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }
    environment {
        DOCKERHUB = credentials('docker-cred')
    }
        
    stage('Build image') {
  
       app = docker.build("harshmandhu/test")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${DOCKERHUB}")
        }
    }
    
}
