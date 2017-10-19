// Declarative //
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building..'
                sh 'cd webdemo && ./gradlew build'
            }

        }

        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'cd webdemo && ./gradlew build'

            }
        }

        
        
        stage('SonarQube analysis') {
           steps {
               echo "starting codeAnalyze with SonarQube......"
               script{
               def sonarqubeScannerHome = tool name:'QaWorkshooScanner'
               withSonarQubeEnv('QaworkshopTest') {
                   sh "${sonarqubeScannerHome}/bin/sonar-scanner"
               }
            
               timeout(4) { 
                   //利用sonar webhook功能通知pipeline代码检测结果，未通过质量阈，pipeline将会fail
                   def qg = waitForQualityGate() 
                       if (qg.status != 'OK') {
                           error "未通过Sonarqube的代码质量阈检查，请及时修改！failure: ${qg.status}"
                       }
                   }
               }
           }


       }
        

            }
        }



