pipeline {
    agent any

    stages {
        stage('Get Build Number') {
            steps {
                script {
                    // Execute the first curl command to get the build number
                    def getBuildNumberCmd = """
                        curl --location --request GET "http://localhost:8085/job/sample/job/master/lastSuccessfulBuild/buildNumber/api/json" --header "Authorization: Basic TWFkaGF2aTptb2tzaGFAOTg=" --header "Cookie: JSESSIONID.4dd3ed8c=node0ai57drd19zwa1i56kwbkrk3lg3.node0"
                    """
                    def buildNumber = bat(script: getBuildNumberCmd, returnStatus: true).trim()
                    echo "Build Number: ${buildNumber}"

                    
                }
            }
        }
    }
}
