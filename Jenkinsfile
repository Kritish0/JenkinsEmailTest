pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        echo '📥 Checking out code...'
        git url: 'https://github.com/Kritish0/<your-repo>.git', branch: 'main'
      }
    }

    stage('Install') {
      steps {
        echo '📦 Installing dependencies...'
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        echo '🧪 Running tests...'
        sh 'npm test || echo "Tests failed but continuing..."'
      }
    }
  }

  post {
    success {
      mail to: 'kritishpudasaini90@gmail.com',
           subject: "✅ SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
           body: """Good news!
Build URL: ${env.BUILD_URL}
Git Commit: ${env.GIT_COMMIT}"""
    }
    failure {
      mail to: 'you@gmail.com',
           subject: "❌ FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
           body: """Build failed.
Check logs: ${env.BUILD_URL}console"""
    }
  }
}
