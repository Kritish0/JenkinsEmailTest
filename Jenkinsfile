pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        // Use the repository configured in the job (no hardcoded URL)
        checkout scm
        echo '📥 Code checked out from job SCM.'
      }
    }

    stage('Install') {
      steps {
        sh 'npm --version || true'
        echo '📦 (Your install step goes here)'
      }
    }

    stage('Test') {
      steps {
        echo '🧪 (Your test step goes here)'
      }
    }
  }

  post {
    success {
      mail to: 'kritishpudasaini90@example.com',
           subject: "✅ SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
           body: """Build succeeded.

Job: ${env.JOB_NAME}
Build: #${env.BUILD_NUMBER}
URL: ${env.BUILD_URL}"""
    }
    failure {
      mail to: 'you@example.com',
           subject: "❌ FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
           body: """Build failed.

Check logs: ${env.BUILD_URL}console"""
    }
  }
}
