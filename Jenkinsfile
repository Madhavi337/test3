

pipeline {
    agent any

    stages {
        stage('Get Build Number') {
            steps {
                script {
                    def response = httpRequest(
                        url: 'http://localhost:8085/job/sample/job/master/lastSuccessfulBuild/buildNumber/api/json',
                        httpMode: 'GET',
                        customHeaders: [
                            [name: "Authorization", value: "Basic TWFkaGF2aTptb2tzaGFAOTg="],
                            [name: "Cookie", value: "JSESSIONID.4dd3ed8c=node0ai57drd19zwa1i56kwbkrk3lg3.node0"]
                        ],
                        responseHandle: 'NONE',
                        timeout: 60,
                        validResponseCodes: '200',
                        ignoreSslErrors: true,
                    )

                    // Check if the HTTP request was successful
                    if (response.status == 200) {
                        def buildNumber = response.getContent()
                        echo "Build Number: ${buildNumber}"

                        stage('Prepare Workspace') {
                            
                                cleanWs()
                            
                        }
                        
                        // Trigger the rebuild as an HTTP request
                        def rebuildResponse = httpRequest(
                            url: "http://localhost:8085/job/sample/job/master/167/rebuild",
                            httpMode: 'GET',
                            customHeaders: [
                                [name: "Authorization", value: "Basic TWFkaGF2aTptb2tzaGFAOTg="],
                                [name: "Cookie", value: "JSESSIONID.4dd3ed8c=node01lzbzk4zdxup81bu3t8onxsw168.node0; JSESSIONID.d107a756=node01tw654ksf9i0ljd6cc9btuklu16.node0"]
                            ],
                            responseHandle: 'NONE',
                            timeout: 60,
                            validResponseCodes: '200',
                            ignoreSslErrors: true,
                        )
                        
                        // Check if the rebuild request was successful
                        if (rebuildResponse.status == 200) {
                            echo "Rebuild request successful"
                        } else {
                            error "Failed to trigger the rebuild (HTTP status ${rebuildResponse.status})"
                        }
                    } else {
                        error "Failed to retrieve the build number (HTTP status ${response.status})"
                    }
                }
            }
        }
    }
}
