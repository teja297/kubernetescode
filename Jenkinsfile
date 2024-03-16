node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

        stage("Build Dokcer Image") {
        script{
             sh "docker build -t teja297/teja-app:5 ."

        }
    }


      stage("dockerlogin push") {
        script{
             sh "docker login -u teja297 -p Teja@7566"
             sh "docker push teja297/teja-app:5"

        }
    }

    
    stage('Trigger ManifestUpdate') {
                echo "triggering updatemanifestjob"
                build job: 'updatemanifest', parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
        }
}
