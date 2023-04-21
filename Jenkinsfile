pipeline {
      environment {
        
        target_url="http://192.168.228.132:81"
        Nmap="192.168.228.132"
        
    }
    
    agent any
   
    stages {
        stage('Checkout using SOURCE_BRANCH') {
             
            steps { 
             git branch: 'master', url: 'https://Mukeshit91@bitbucket.org/Mukeshit91/dvpwa.git'
   }
        }
        stage('Generating SBOM') {
             
            steps { 
             //sh 'pip install cyclonedx-bom'
             sh 'sudo rm sbom.xml ||true'
             sh 'python3 -m cyclonedx_py -r -o sbom.xml'
             
   }
        }
        stage('Sbom push to Dtrack') {
              
            steps {
                 script {
                     
               // dependencyTrackPublisher artifact: 'sbom.xml', autoCreateProjects: true, dependencyTrackApiKey: 'dtrack-1', dependencyTrackFrontendUrl: 'http://192.168.228.132:8085', dependencyTrackUrl: 'http://192.168.228.132:8081', overrideGlobals: true, projectId: '63753780-e778-476e-ab4e-0fd6f01e6fd7', projectName: 'abc', projectVersion: '', synchronous: true
                 // dependencyTrackPublisher artifact: 'target/bom.json', autoCreateProjects: true, dependencyTrackApiKey: 'dtrack-1', dependencyTrackFrontendUrl: 'http://3.21.165.77:8080', dependencyTrackUrl: 'http://3.21.165.77:8081', overrideGlobals: true, projectId: '86c2908c-6463-4135-b4de-fdb84dd38238', projectName: 'demo', projectVersion: '', synchronous: true
                 dependencyTrackPublisher artifact: 'sbom.xml', autoCreateProjects: true, dependencyTrackApiKey: 'Dtrack_cred', dependencyTrackFrontendUrl: 'http://192.168.228.132:8085', dependencyTrackUrl: 'http://192.168.228.132:8085', overrideGlobals: true, projectId: 'c663e1c5-b669-46e4-9a46-967d06c296ab', synchronous: true
                     
                 }
                
                }
            }
    }
}
