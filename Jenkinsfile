pipeline {
  agent {
    label {
      label 'QA2'
    }
  }
  stages {
    stage ('one') {
      steps {
        sh '''sudo docker kill c2 || true
        sudo docker rm c2 || true
        sudo cp /mnt/jenkins-slave/workspace/jd2/index.html /mnt/lol/
        sudo docker run -itdp 90:80 -v /mnt/lol:/usr/local/apache2/htdocs --name c2 --network=velocity httpd
        sudo docker exec -d c2 sh -c "chmod 644 /usr/local/apache2/htdocs/index.html"'''
      }
    }
  }
  post {
    always {
      sh "rm -rf ${WORKSPACE}/*"
    }
  }
}
