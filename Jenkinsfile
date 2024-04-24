pipeline {
    agent any
    environment {
        PATH = "${PATH}:${getTerraformPath()}"
        ACTION = "destroy"
        RUNNER = "Isaac"
    }

    stages{
        stage('Initial Deployment Approval') {
              steps {
                script {
                def userInput = input(id: 'confirm', message: 'Start Pipeline?', parameters: [ [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Start Pipeline', name: 'confirm'] ])
             }
           }
        }

         stage('terraform init'){
             steps {
                slackSend (color: '#FFFF00', message: "STARTED Init: Job by ${RUNNER} - '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
                sh "terraform init"
             }
         }

         stage('terraform force-unlock ac0948c7-f3a6-3835-ae31-788f452ccbfa')
            steps {
                sh "terraform force-unlock ac0948c7-f3a6-3835-ae31-788f452ccbfa"
            }

        //  stage('terraform plan'){
        //     steps {
        //         // sh "terraform plan --auto-approve"
        //         slackSend (color: '#FFFF00', message: "STARTED Plan: Job by ${RUNNER} - '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
        //         sh "terraform plan -out=tfplan -input=false"
        //     }
        // }

        //  stage('Final Deployment Approval') {
        //     steps {
        //         script {
        //             def userInput = input(id: 'confirm', message: 'Apply Terraform?', parameters: [ [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Apply terraform', name: 'confirm'] ])
        //         }
        //     }
        //  }

        // stage('Terraform Final Action'){
        //     steps {
        //         slackSend (color: '#FFFF00', message: "STARTED Apply: Job by ${RUNNER} - '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
        //         script{stage("Performing Terraform ${ACTION}")}
        //         sh "terraform ${ACTION} --auto-approve"
        //         //  sh "terraform apply  -input=false tfplan"
        //     }
        // }

        // stage('Terraform Destroy'){
        //     steps {
        //          sh "terraform destroy -auto-approve"
        //     }
        // }
    }
}

def getTerraformPath(){
        def tfHome = tool name: 'terraform-40', type: 'terraform'
        return tfHome
}
