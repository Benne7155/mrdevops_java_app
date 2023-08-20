@Library ('my-shared-library') _
pipeline{  

  agent any
  parameters{
     
     choice(name: 'action', choices: 'create\ndelete', description: 'create/destory')
  }

  stages{

    stage('git checkout'){
    when { expression{ params.action == 'create'} }

        steps{

            script{ 
                gitCheckout(
                  branch: "feature",
                  url: "https://github.com/Benne7155/mrdevops_java_app.git"
                )
            }

        }
    }
    stage('Unit Test Maven'){
    when { expression{ params.action == 'create'} }

        steps{

            script{ 
               mvnTest() 
            }
        }
  }
    stage('Integration Test Maven'){
    when { expression{ params.action == 'create'} }


        steps{

            script{ 
              mvnintegrationTest() 
            }
        }
  }

  stage('static code analysis :sonar'){
  when { expression{ params.action == 'create'} }


        steps{

            script{ 
              def SonarcubecredentialsId = 'sonar-api'
              staticcodeanalysis(SonarcubecredentialsId) 
            }
        }
  }

  stage('Quality gate status check :sonar'){
  when { expression{ params.action == 'create'} }


        steps{

            script{ 
              def SonarcubecredentialsId = 'sonar-api'
              QualityGateStatus(SonarcubecredentialsId) 
            }
        }
  }
  }
}