@Library ('my-shared-library') _
pipeline{  

  agent any
  parameters{
     
     choice(name: 'action', choices: 'create\ndelete', description: 'create/destory')
  }

  stages{

    when { expression{ param.action == 'create'} }

    stage('git checkout'){

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
    
    when { expression{ param.action == 'create'} }

        steps{

            script{ 
               mvnTest() 
            }
        }
  }
    stage('Integration Test Maven'){
    
    when { expression{ param.action == 'create'} }


        steps{

            script{ 
              mvnintegrationTest() 
            }
        }
  }

  stage('static code analysis :sonar'){
    
    when { expression{ param.action == 'create'} }


        steps{

            script{ 
              staticcodeanalysis() 
            }
        }
  }
}
}