pipeline {
    agent {
        label "master"
    }
    stages {
        stage("clean-up"){
            steps{
                sh "mvn clean"
            }
        }
	stage("test"){
            steps{
                sh "mvn test"
            }
        }
	stage("package"){
            steps{
                sh "mvn package"
            }
        }
    }
    post {
        always{
            mail to: 'shubhamguptacloud@gmail.com',
			subject: "Pipeline: ${currentBuild.fullDisplayName} is ${currentBuild.currentResult}",
			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
        }
         success {
            echo "Packaging successful"
        }
        failure {
            echo "Packaging unsuccessful"
        }
    }
}
