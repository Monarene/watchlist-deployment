def region = 'us-east-2'
def accounts = [master:'production', preprod:'staging', develop:'sandbox-test']

node('') {
    stage('Checkout'){
            checkout scm
}

 stage('Authentication'){
        sh "aws eks update-kubeconfig --name ${accounts[env.BRANCH_NAME]} --region ${region}"
    }

    stage('Deploy'){
        sh 'kubectl apply -f deployments/'
    }
}