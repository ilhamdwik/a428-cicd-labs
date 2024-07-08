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

        stage('Manual Approval') {
            input "Lanjutkan ke tahap Deploy?"
        }

        stage('Deploy') {
            // Execute the deliver script inside the Docker container
            sh './jenkins/scripts/deliver.sh'
            // Add sleep for 60 seconds
            sleep 60
            sh './jenkins/scripts/kill.sh'
        }
    }
}

// Scripted Pipeline
// node {
//     // Using Docker with specific image and arguments
//     docker.image('node:16-buster-slim').inside('-p 3000:3000') {
//         stage('Build') {
//             // Execute npm install inside the Docker container
//             sh 'npm install'
//         }

//         stage('Test') {
//             // Execute the test script inside the Docker container
//             sh './jenkins/scripts/test.sh'
//         }

//         stage('Manual Approval') {
//             // Execute the test script inside the Docker container
//             input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)' 
//             sh './jenkins/scripts/kill.sh'
//         }

//         stage('Deploy') {
//             // Execute the test script inside the Docker container
//             sh './jenkins/scripts/deliver.sh'
//             sleep 60
//             input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)' 
//             sh './jenkins/scripts/kill.sh' 
//         }
//     }
// }

// Declarative Pipeline
// pipeline {
//     agent {
//         docker {
//             image 'node:lts-buster-slim'
//             args '-p 3000:3000'
//         }
//     }
//     environment {
//         CI = 'true'
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
//         stage('Deliver') {
//             steps {
//                 sh './jenkins/scripts/deliver.sh'
//                 input message: 'Finished using the website? (Click "Proceed" to continue)'
//                 sh './jenkins/scripts/kill.sh'
//             }
//         }
//     }
// }

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
