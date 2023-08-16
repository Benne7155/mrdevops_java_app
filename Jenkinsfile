@Library ('my-shared-library') _
pipeline{  

  agent any

  stages{

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

  }
}