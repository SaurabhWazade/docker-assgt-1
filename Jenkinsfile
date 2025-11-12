pipeline {
  agent {
    label {
      label 'QA1'
    }
  }
  stages {
    stage ('one') {
      steps {
        sh '''sudo docker kill c1 || true
        sudo docker rm c1 || true
        sudo cp /root/.jenkins/workspace/jd1/index.html /mnt/lol1/
        sudo docker run -itdp 80:80 -v /mnt/lol:/usr/local/apache2/htdocs --name c1 --network=velocity httpd
        sudo docker exec -d c1 sh -c "chmod 644 /usr/local/apache2/htdocs/index.html"'''
      }
    }
  }
  post {
    always {
      sh "rm -rf ${WORKSPACE}/*"
    }
  }
}
