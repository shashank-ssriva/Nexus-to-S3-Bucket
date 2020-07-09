node {
    stage('Pull the file off Nexus') {
        withCredentials([usernameColonPassword(credentialsId: 'nexus-admin-user', variable: 'NEXUS_CREDENTIALS')]) {
            sh label: '', script: 'curl -u ${NEXUS_CREDENTIALS} -o 20200708_101553.png "http://nexus-server:8083/repository/s3-repo/photos/20200708_101553.png"'
        }
    }

    stage('Upload file(s) to S3') {
            withAWS(region:'ap-south-1',credentials:'aws_root') {
                s3Upload(bucket:"mysuperbucket-shashank", file:'20200708_101553.png');
            }
    }
}
