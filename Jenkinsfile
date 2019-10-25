// Every jenkins file should start with either a Declarative or Scripted Pipeline entry point.
node {
    try {
        //Call function to send a message to Slack
        notifyBuild('STARTED')
        // Global variable declaration
        def project = 'sa-android'
        def appName = 'Sample App'

        // Stage, is to tell the Jenkins that this is the new process/step that needs to be executed
        stage('Checkout') {
            // Pull the code from the repo
            checkout scm
        }

        stage('Build Image') {
            // Build our docker Image
            sh("assembleDebug")
        }

        stage('Run application test') {
            sh("test")
        }

    } catch (e) {
        currentBuild.result = "FAILED"
        throw e
      } finally {
        //notifyBuild(currentBuild.result)
    }
}

