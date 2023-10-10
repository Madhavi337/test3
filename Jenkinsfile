pipeline {
    agent any

    stages {
        stage('Get Build Number') {
            steps {
                script {
                    // Execute the first curl command to get the build number
                    def getBuildNumberCmd = """
                        curl --location --request GET 'http://localhost:8085/job/sample/job/master/lastSuccessfulBuild/buildNumber/api/json' ^
                        --header 'Authorization: Basic TWFkaGF2aTptb2tzaGFAOTg=' ^
                        --header 'Cookie: JSESSIONID.5ae62df6=node01et9dq0uxrvg61q9ta2v3y672a44.node0; JSESSIONID.4dd3ed8c=node01lzbzk4zdxup81bu3t8onxsw168.node0; JSESSIONID.d107a756=node01hf1fb4987iy7z1zzghynju766.node0' ^
                        --header 'Accept: application/json'
                    """
                    def buildNumber = bat(script: getBuildNumberCmd, returnStatus: true).trim()
                    echo "Build Number: ${buildNumber}"

                    // Execute the second curl command with the build number
                    def rebuildCmd = """
                        curl --location --request GET 'http://localhost:8085/job/sample/job/master/${buildNumber}/rebuild' ^
                        --header 'Accept: application/json' ^
                        --header 'Authorization: Basic TWFkaGF2aTptb2tzaGFAOTg=' ^
                        --header 'Cookie: JSESSIONID.4dd3ed8c=node01lzbzk4zdxup81bu3t8onxsw168.node0; JSESSIONID.d107a756=node01hf1fb4987iy7z1zzghynju766.node0'
                    """
                    bat(script: rebuildCmd)
                }
            }
        }
    }
}
