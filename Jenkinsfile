// Every jenkins file should start with either a Declarative or Scripted Pipeline entry point.
node {
    try {
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

