pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'rm -rf build'   //  remove build folder
                sh 'mkdir build'    // create a new folder
                sh 'touch build/car.txt'    // create a empty file
                sh 'echo "chassis" >> build/car.txt' // put chassis inside the file
                sh 'echo "engine" >> build/car.txt'  //put engine inside the file
                sh 'echo "body" >> build/car.txt'
            }
        }
        stage('Test'){
            steps {
                sh 'test -f build/car.txt'  // test command combined with the -f flag allow us to test if a file exists
                sh 'grep "chassis" build/car.txt'   // grep command will enable us to search the content of a file for a specific string
                sh 'grep "engine" build/car.txt'
                sh 'grep "body" build/car.txt'
            }
        }
        stage('Publish'){
            steps {
                archiveArtifacts artifacts: 'build/' 
            }
        }
    }
}
