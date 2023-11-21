pipeline {
        agent any
        tools {
            // Install the Maven version configured as "M3" and add it to the path.
            maven "M3"
        }

        stages {
            stage('Checkout') {
                steps {
                    // Get some code from a GitHub repository
                    echo 'Getting code from the requested GitHub respository bear with'
                    git branch: 'main', url: 'https://github.com/heapsofcod/lbg-hello-world-maven'
                }
            }
            stage('Compile') {
                steps {
                    // Run Maven on a Unix agent.
                    sh "mvn clean compile"
                }
            }
            stage('Test') {
                steps {
                    echo 'Run the unit tests'
                    catchError {
                        sh "mvn test"
                    }
                }
            }
            stage('Package') {
                steps {
                    sh "mvn -Dmaven.test.skip -Dmaven.compile.skip package"
                }
            }
            stage('Print: Well Done Rhian') {
                steps {
                    echo "Well Done Rhian. You ROCK."
                }
            }
        }
}