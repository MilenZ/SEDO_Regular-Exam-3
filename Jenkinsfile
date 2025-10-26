pipeline{
    agent any
    triggers {
        githubPush()
        // pollSCM('H/2 * * * *')
    }
    stages{
        stage("Restore .Net Packages"){
            when { branch 'main' }
            steps{
                bat 'dotnet restore'
            }
        }
        stage("Build .Net Project"){
            when { branch 'main' }
            steps{
                bat 'dotnet build --no-restore'
            }
        }
        stage("Run UNIT Tests"){
            when { branch 'main' }
            steps{
                bat 'dotnet test --no-build'
            }
        }
    }
    post {
        always {
        echo "Build finished with status: ${currentBuild.currentResult}"
        }
    }
}