pipeline {
    agent any
    tools {nodejs "nodejs"}
    
    environment {
		scannerHome = tool 'Sonar-Scanner'
    }
    
    stages { 
    	stage('prep') {
    		steps{
        		git url: 'http://172.29.113.80/reingenieria-cotizadores/api-vehicular-brokers.git'                
	        }		
    	}   
        stage('Install dependencies') {
            steps {
                //sh 'rm package-lock.json'
    		    sh 'npm install'
    		    sh 'npm install newman'
            }
        } 
        stage('SonarTest'){
	    steps{
	    	echo '1'
		//withSonarQubeEnv('SonarQubeServer') {
			//sh "${scannerHome}/bin/sonar-scanner -e  -Dsonar.host.url=http://172.29.113.232:10003 -Dsonar.login=${sonarLogin}  -Dsonar.projectName=api-vida-project-test -Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=api-vida-project-test -Dsonar.sources=src"
		//	sh """${scannerHome}/bin/sonar-runner -D sonar.login=jpaez-paez -D sonar.password=jorge-paez"""
		//}
            }
        }                       
        stage('Test') {
	      steps {
	        script {
	          sh 'npm run test'
	        }
	      }
	      /*post {
	        always {
	          step([$class: 'CoberturaPublisher', coberturaReportFile: 'output/coverage/jest/cobertura-coverage.xml'])
	        }
	      }*/
	    }
        /*
        stage('deploy-desa') {
			when { 
				environment name: 'STAGE_DEPLOY', value: 'DESA' 
			}
			steps {
                sh 'serverless deploy --stage $STAGE_DEPLOY --aws-profile account-cotizadores'
			}
		}*/
    }
}
