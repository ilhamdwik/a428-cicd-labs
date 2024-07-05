// Scripted Pipeline
node {
    // Using Docker with specific image and arguments
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {
        stage('Build') {
            // Execute npm install inside the Docker container
            sh 'npm install'
        }

        stage('Test') {
            // Execute the test script inside the Docker container
            sh './jenkins/scripts/test.sh'
        }
    }
}



// Declarative Pipeline
// pipeline {
//     agent {
//         docker {
//             image 'node:16-buster-slim'
//             args '-p 3000:3000'
//         }
//     }
//     stages {
//         stage('Build') {
//             steps {
//                 sh 'npm install'
//             }
//         }
//         stage('Test') { 
//             steps {
//                 sh './jenkins/scripts/test.sh' 
//             }
//         }
//     }
// }
