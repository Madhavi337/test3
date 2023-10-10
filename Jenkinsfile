pipeline {
    agent any

    stages {
        stage('Get Build Number') {
            steps {
                script {


                    // def response = httpRequest(
                    //         url: 'http://localhost:8085/job/sample/job/master/lastSuccessfulBuild/buildNumber/api/json',
                    //         httpMode: 'GET',
                    //         customHeaders: [[name: "Authorization", value: "TWFkaGF2aTptb2tzaGFAOTg="],[name: "Cookie", value: "JSESSIONID.4dd3ed8c=node0ai57drd19zwa1i56kwbkrk3lg3.node0"]],
                    //         responseHandle: 'NONE',
                    //         timeout: 60,
                    //         validResponseCodes: '200',
                    //         ignoreSslErrors: true,
                    //     )

                    // def statusCode = response.getStatus()
                    //     def responseBody = response.getContent()

                    //     echo "Response Status Code: ${statusCode}"
                    //     echo "Response Body: ${responseBody}"

                    // Execute the first curl command to get the build number
                    def getBuildNumberCmd = """
                        curl --location --request GET "http://localhost:8085/job/sample/job/master/lastSuccessfulBuild/buildNumber/api/json" --header "Authorization: Basic TWFkaGF2aTptb2tzaGFAOTg=" --header "Cookie: JSESSIONID.4dd3ed8c=node0ai57drd19zwa1i56kwbkrk3lg3.node0"
                    """
                    

                    
                }
            }
        }
    }
}
