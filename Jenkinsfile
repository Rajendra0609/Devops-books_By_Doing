pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    def userInput = input(id: 'ctns-prompt', message: 'Continue to the next stage?', ok: 'Proceed')
                    echo "User chose: ${userInput}"
                }
            }
        }
        stage('Next Stage') {
            steps {
                echo 'This is the next stage.'
            }
        }
    }
}
###################################################################
pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    def userInput = input(
                        id: 'ctns-prompt', 
                        message: 'Continue to the next stage?', 
                        ok: 'Yes', 
                        submitter: 'user1,user2'
                    )
                    echo "User chose: ${userInput}"
                }
            }
        }
        stage('Next Stage') {
            steps {
                echo 'This is the next stage.'
            }
        }
    }
}
#############################################################################
pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Store the approving submitter
                    def resp = input(
                        id: 'ctns-prompt', 
                        message: 'Continue to the next stage?', 
                        ok: 'Yes', 
                        submitter: 'rani,Hd', 
                        submitterParameter: 'approver'
                    )
                    echo "Answered by ${resp}"
                }
            }
        }
        stage('Next Stage') {
            steps {
                echo 'This is the next stage.'
            }
        }
    }
}
#################################################

pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Store the approving submitter and additional parameters
                    def resp = input(
                        id: 'ctns-prompt', 
                        message: 'Continue to the next stage?',
                        parameters: [string(defaultValue: '', description: '', name: 'para1')],
                        submitter: 'rani,HD', 
                        submitterParameter: 'approver'
                    )
                    echo "Answered by " + resp['approver']
                }
            }
        }
        stage('Next Stage') {
            steps {
                echo 'This is the next stage.'
            }
        }
    }
}
############################################################
pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Store the approving submitter and additional parameters
                    def resp = input(
                        id: 'ctns-prompt', 
                        message: 'Continue to the next stage?',
                        parameters: [string(defaultValue: '', description: '', name: 'para1')],
                        submitter: 'rani,HD', 
                        submitterParameter: 'approver'
                    )
                    echo "Answered by " + resp['approver']
                    // Store parameter value
                    env.PARA1 = resp['para1']
                }
            }
        }
        stage('Next Stage') {
            steps {
                echo 'This is the next stage.'
                echo "Parameter value: ${env.PARA1}"
            }
        }
    }
}
#########################################################
pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Store the approving submitter and additional parameters
                    def resp = input(
                        id: 'ctns-prompt', 
                        message: 'Continue to the next stage?',
                        parameters: [
                            string(defaultValue: '', description: '', name: 'para1'),
                            choice(choices: ['release', 'Prerelease', 'test'], description: 'Choose action', name: 'action')
                        ],
                        submitter: 'rani,HD', 
                        submitterParameter: 'approver'
                    )
                    echo "Answered by " + resp['approver']
                    // Store parameter values
                    env.PARA1 = resp['para1']
                    env.ACTION = resp['action']
                }
            }
        }
        stage('Next Stage') {
            steps {
                echo 'This is the next stage.'
                echo "Parameter value: ${env.PARA1}"
                echo "Chosen action: ${env.ACTION}"
            }
        }
    }
}
#########################################################################

pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Store the approving submitter and additional parameters
                    def resp = input(
                        id: 'ctns-prompt', 
                        message: 'Continue to the next stage?',
                        parameters: [
                            string(defaultValue: '', description: '', name: 'para1'),
                            choice(choices: ['release', 'test'], description: 'Choose action', name: 'action')
                        ],
                        submitter: 'rani,HD', 
                        submitterParameter: 'approver'
                    )
                    echo "Answered by " + resp['approver']
                    // Store parameter values
                    env.PARA1 = resp['para1']
                    env.ACTION = resp['action']
                }
            }
        }
        stage('Release Stage') {
            when {
                expression { env.ACTION == 'release' }
            }
            steps {
                echo 'This is the release stage.'
                // Add your release-specific steps here
            }
        }
        stage('Test Stage') {
            when {
                expression { env.ACTION == 'test' }
            }
            steps {
                echo 'This is the test stage.'
                // Add your test-specific steps here
            }
        }
    }
}
######################################################################
pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Store the user choice
                    def userChoice = input(
                        message: 'Continue to the next stage?',
                        parameters: [
                            choice(choices: "release\ntest\n", description: 'Choose an action', name: 'action')
                        ],
                        submitter: 'rani,HD', 
                        submitterParameter: 'approver'
                    )
                    echo "Answered by ${userChoice['approver']}"
                    echo "Chosen action: ${userChoice['action']}"
                    // Store the chosen action
                    env.ACTION = userChoice['action']
                }
            }
        }
        stage('Release Stage') {
            when {
                expression { env.ACTION == 'release' }
            }
            steps {
                echo 'This is the release stage.'
                // Add your release-specific steps here
            }
        }
        stage('Test Stage') {
            when {
                expression { env.ACTION == 'test' }
            }
            steps {
                echo 'This is the test stage.'
                // Add your test-specific steps here
            }
        }
    }
}
####################################################################

pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Store the user choice
                    def userChoice = input(
                        message: 'Continue to the next stage?',
                        parameters: [
                            choice(choices: "choice1\nchoice2\nchoice3\nchoice4", description: 'Choose an option', name: 'Options')
                        ]
                    )
                    echo "Chosen option: ${userChoice}"
                    // Store the chosen option
                    env.OPTION = userChoice
                }
            }
        }
        stage('Choice1 Stage') {
            when {
                expression { env.OPTION == 'choice1' }
            }
            steps {
                echo 'This stage runs if choice1 is selected.'
            }
        }
        stage('Choice2 Stage') {
            when {
                expression { env.OPTION == 'choice2' }
            }
            steps {
                echo 'This stage runs if choice2 is selected.'
            }
        }
        stage('Choice3 Stage') {
            when {
                expression { env.OPTION == 'choice3' }
            }
            steps {
                echo 'This stage runs if choice3 is selected.'
            }
        }
        stage('Choice4 Stage') {
            when {
                expression { env.OPTION == 'choice4' }
            }
            steps {
                echo 'This stage runs if choice4 is selected.'
            }
        }
    }
}
###############################################################

pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Request user input for SSH key credentials
                    def creds = input(
                        message: 'Continue to the next stage?',
                        parameters: [[$class: 'CredentialsParameterDefinition', 
                                      credentialType: 'com.cloudbees.jenkins.plugins.sshcredentials.impl.BasicSSHUserPrivateKey', 
                                      defaultValue: 'jenkins2-ssh', 
                                      description: 'SSH key for access', 
                                      name: 'SSH', 
                                      required: true]]
                    )
                    echo "Selected credentials: ${creds}"
                    // Store the credentials ID
                    env.SSH_CREDENTIALS = creds
                }
            }
        }
        stage('Use SSH Key') {
            steps {
                echo 'This stage uses the selected SSH key.'
                // Use the SSH credentials ID
                withCredentials([sshUserPrivateKey(credentialsId: env.SSH_CREDENTIALS, keyFileVariable: 'SSH_KEY')]) {
                    sh 'echo Using SSH key from ${SSH_KEY}'
                    // Add your steps that require the SSH key here
                }
            }
        }
    }
}

###############################################################################################

pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Request user input for file upload
                    def selectedFile = input(
                        message: 'Upload a file to continue to the next stage',
                        parameters: [file(description: 'Choose file to upload', name: 'local')]
                    )
                    echo "Selected file: ${selectedFile}"
                    // Store the file path
                    env.UPLOADED_FILE = selectedFile
                }
            }
        }
        stage('Process Uploaded File') {
            steps {
                echo 'Processing the uploaded file.'
                // Use the uploaded file
                sh 'cat $UPLOADED_FILE'  // Example: Display the content of the uploaded file
            }
        }
    }
}
#####################################################
pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Request multi-line text input
                    def lines = input(
                        message: 'Please enter multiple lines of text:',
                        parameters: [text(defaultValue: '''line 1
line 2
line 3''', description: 'Enter your text here', name: 'Input Lines')]
                    )
                    echo "User input: ${lines}"
                    // Store the input lines
                    env.INPUT_LINES = lines
                }
            }
        }
        stage('Process Input Lines') {
            steps {
                echo 'Processing the input lines.'
                // Use the input lines
                echo "Received lines: ${env.INPUT_LINES}"
            }
        }
    }
}
###############################3
pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Request user input for password
                    def pw = input(
                        message: 'Please enter your password:',
                        parameters: [password(defaultValue: '', description: 'Enter your password.', name: 'passwd')]
                    )
                    // Echoing passwords is not a good practice, use the password securely in your steps
                    echo "Password has been securely entered."
                    // Store the password securely
                    env.USER_PASSWORD = pw
                }
            }
        }
        stage('Use Password') {
            steps {
                echo 'This stage uses the entered password securely.'
                // Use the password securely in your steps
                sh 'echo Using password securely.'
            }
        }
    }
}
##########################################################
pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('User Input') {
            steps {
                script {
                    // Request user input for selecting a run and entering a string
                    def selection = input(
                        message: 'Please make your selections:',
                        parameters: [
                            [$class: 'RunParameterDefinition', description: 'Choose a run of the project', 
                             filter: 'ALL', name: 'RUN', projectName: 'pipe1'],
                            string(defaultValue: '', description: 'Enter response', name: 'Response')
                        ]
                    )
                    echo "Selection is ${selection['RUN']}"
                    echo "User response: ${selection['Response']}"
                    // Store the selected run and response
                    env.SELECTED_RUN = selection['RUN']
                    env.USER_RESPONSE = selection['Response']
                }
            }
        }
        stage('Process Run and Response') {
            steps {
                echo 'Processing the selected run and user response.'
                // Use the selected run and response
                echo "Selected run: ${env.SELECTED_RUN}"
                echo "User response: ${env.USER_RESPONSE}"
            }
        }
    }
}


#######################################################

pipeline {
    agent any

    stages {
        stage('Initial Stage') {
            steps {
                echo 'This is the initial stage.'
            }
        }
        stage('Login Stage') {
            steps {
                script {
                    // Request user input for login information
                    def loginInfo = input(
                        message: 'Login',
                        parameters: [
                            string(defaultValue: '', description: 'Enter Userid:', name: 'userid'),
                            password(defaultValue: '', description: 'Enter Password:', name: 'passwd')
                        ]
                    )
                    // Print statements to show different ways to access the individual return values
                    echo "Username = " + loginInfo['userid']
                    echo "Password = ${loginInfo['passwd']}"
                    echo loginInfo.userid + " " + loginInfo.passwd
                    // Store the user input securely
                    env.USER_ID = loginInfo['userid']
                    env.USER_PASSWORD = loginInfo['passwd']
                }
            }
        }
        stage('Use Credentials') {
            steps {
                echo 'This stage uses the entered credentials securely.'
                // Use the credentials securely in your steps
                script {
                    sh """
                    echo 'Using credentials securely.'
                    # Perform actions requiring the credentials securely here
                    # Example: using credentials in a command
                    some_command --userid ${env.USER_ID} --password ${env.USER_PASSWORD}
                    """
                }
            }
        }
    }
}
########################
pipeline {
    agent any
    parameters {
        string(name: 'USERID', defaultValue: '', description: 'Enter your userid')
    }
    stages {
        stage('Login') {
            steps {
                echo "Active user is now ${params.USERID}"
            }
        }
    }
}
###############################
pipeline {
    agent any
    environment {
        // Environment variables
        JAVA_HOME = "/usr/lib/jvm/java-11-openjdk"
        MAVEN_HOME = "/opt/maven"
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }
    tools {
        // Use Maven and JDK installations
        maven 'Maven 3.6.3'
        jdk 'JDK 11'
    }
    options {
        // Keep only the last 10 builds
        buildDiscarder(logRotator(numToKeepStr: '10'))
        // Add timestamps to the console output
        timestamps()
        // Show the pipeline stages in a visualized format
        ansiColor('xterm')
    }
    triggers {
        // Trigger builds on SCM changes
        scm('H/5 * * * *')
    }
    parameters {
        // Define parameters for the build
        string(name: 'BRANCH', defaultValue: 'main', description: 'Branch to build')
    }
    libraries {
        // Load shared libraries
        lib('shared-library')
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                checkout([$class: 'GitSCM', branches: [[name: "${params.BRANCH}"]], userRemoteConfigs: [[url: 'https://github.com/your-repo.git']]])
            }
        }
        stage('Build') {
            steps {
                // Build the project
                sh 'mvn clean install'
            }
            post {
                success {
                    // Archive the built artifacts
                    archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
                }
                failure {
                    // Notify on build failure
                    mail to: 'dev-team@example.com',
                         subject: "Build Failed: ${currentBuild.fullDisplayName}",
                         body: "The build has failed. Please check the Jenkins job for details."
                }
            }
        }
        stage('Test') {
            steps {
                // Run tests
                sh 'mvn test'
            }
            post {
                success {
                    // Archive test results
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deploy') {
            steps {
                // Deploy the application
                sh 'ansible-playbook deploy.yml'
            }
            post {
                always {
                    // Notify on deployment status
                    mail to: 'dev-team@example.com',
                         subject: "Deployment Status: ${currentBuild.fullDisplayName}",
                         body: "Deployment completed. Please check the Jenkins job for details."
                }
            }
        }
    }
    post {
        always {
            // Clean up workspace after build
            cleanWs()
        }
    }
}
#########################################################
pipeline {
    agent any
    stages {
        stage('Input') {
            steps {
                script {
                    def resp = input message: 'Please provide responses:',
                    parameters: [
                        string(defaultValue: '',
                        description: 'Enter response 1',
                        name: 'RESPONSE1'),
                        string(defaultValue: '',
                        description: 'Enter response 2',
                        name: 'RESPONSE2')
                    ]
                    echo "${resp.RESPONSE1}"
                    echo "${resp.RESPONSE2}"
                }
            }
        }
    }
}
#######################################################################

pipeline {
    agent any
    stages {
        stage('Input') {
            steps {
                script {
                    def resp = input message: 'Please provide responses:',
                    parameters: [
                        string(defaultValue: '', description: 'Enter response 1', name: 'RESPONSE1'),
                        string(defaultValue: '', description: 'Enter response 2', name: 'RESPONSE2')
                    ]
                    env.RESP1 = resp.RESPONSE1
                    env.RESP2 = resp.RESPONSE2

                    echo "Response 1: ${env.RESP1}"
                    echo "Response 2: ${env.RESP2}"
                }
            }
        }
    }
}
####################################
@Library('Utilities') _
pipeline {
    agent any
    stages {
        stage('Input') {
            steps {
                script {
                    // Call the getUser function from the Utilities library
                    getUser('Enter response 1', 'Enter response 2')
                }
            }
        }
    }
}
#############################################################################

pipeline {
    agent any

    stages {
        stage('Input') {
            steps {
                script {
                    def response
                    stage('input') {
                        timeout(time: 10, unit: 'SECONDS') {
                            response = input message: 'User',
                            parameters: [string(defaultValue: 'user1',
                            description: 'Enter Userid:', name: 'userid')]
                        }
                        echo "Username = " + response
                    }
                }
            }
        }
    }
}
##########################################################################

pipeline {
    agent any

    stages {
        stage('Input') {
            steps {
                script {
                    def response
                    stage('input') {
                        try {
                            timeout(time: 10, unit: 'SECONDS') {
                                response = input message: 'User',
                                parameters: [string(defaultValue: 'user1',
                                description: 'Enter Userid:', name: 'userid')]
                            }
                        } catch (err) {
                            response = 'user1'
                        }
                        echo "Username = " + response
                    }
                }
            }
        }
    }
}

################################################################
pipeline {
    agent any

    stages {
        stage('Example') {
            steps {
                script {
                    // Retry the block of code <n> times
                    retry(3) { // Adjust <n> to the number of retries you want
                        echo 'Processing...'
                        // Add your processing code here
                    }

                    // Sleep for 5 minutes
                    sleep time: 5, unit: 'MINUTES'

                    // Wait until a condition is met
                    waitUntil {
                        // Replace this with your actual processing code
                        // The code should return true or false
                        def conditionMet = false
                        // Add your condition checking code here
                        if (/* your condition */) {
                            conditionMet = true
                        }
                        return conditionMet
                    }
                    
                    echo 'All steps completed.'
                }
            }
        }
    }
}
##################################################################

pipeline {
    agent any

    stages {
        stage('Check File') {
            steps {
                script {
                    timeout(time: 15, unit: 'SECONDS') {
                        waitUntil {
                            def ret = sh returnStatus: true,
                            script: 'test -e /home/jenkins2/marker.txt'
                            return (ret == 0)
                        }
                    }
                    echo 'File check completed.'
                }
            }
        }
    }
}

#############################################################
pipeline {
    agent any

    stages {
        stage('Prepare') {
            steps {
                script {
                    // Locking a specific node
                    lock('worker_node1') {
                        // Steps to do on worker_node1
                        echo 'Locked worker_node1 for preparation.'
                    }
                }
            }
        }

        stage('Docker Nodes') {
            steps {
                script {
                    // Locking a label with quantity
                    lock(label: 'docker-node', quantity: 3) {
                        // Steps for docker-node
                        echo 'Locked 3 docker-nodes for processing.'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Run the Gradle build on a locked node
                    lock('worker_node1') {
                        sh 'gradle clean build -x test'
                    }
                }
            }
        }
    }
}

##################################################################
pipeline {
    agent any

    stages {
        stage('Prepare') {
            steps {
                script {
                    lock('worker_node1') {
                        echo 'Locked worker_node1 for preparation.'
                    }
                }
            }
        }

        stage('Docker Nodes') {
            steps {
                script {
                    lock(label: 'docker-node', quantity: 3) {
                        echo 'Locked 3 docker-nodes for processing.'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    lock('worker_node1') {
                        sh "'${gradleLoc}/bin/gradle' clean build"
                    }
                }
            }
        }

        // Setting a milestone after the build stage
        milestone label: 'After build', ordinal: 1

        stage('NotifyOnFailure') {
            steps {
                script {
                    // Notify on failure logic goes here
                    // For example, sending an email notification
                    echo 'Build failed. Notifying stakeholders...'
                }
            }
        }
    }
}

###################################################################

pipeline {
    agent any
    options {
        disableConcurrentBuilds()
    }

    stages {
        stage('Build') {
            parallel {
                stage('Unit Tests') {
                    steps {
                        echo 'Running unit tests'
                        // Add your unit test steps here
                    }
                }
                stage('Integration Tests') {
                    steps {
                        echo 'Running integration tests'
                        // Add your integration test steps here
                    }
                }
                stage('Static Analysis') {
                    steps {
                        echo 'Running static analysis'
                        // Add your static analysis steps here
                    }
                }
            }
        }
    }
}
###################################################################

pipeline {
    agent { label 'worker_node1' }

    stages {
        stage('Parallel Demo') {
            steps {
                script {
                    // Define the map for parallel steps
                    def stepsToRun = [:]

                    // Populate the map with steps
                    for (int i = 1; i < 5; i++) {
                        stepsToRun["Step${i}"] = {
                            node {
                                echo "start"
                                sleep 5
                                echo "done"
                            }
                        }
                    }

                    // Run the steps in parallel
                    parallel stepsToRun
                }
            }
        }
    }
}

###########################################################
pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                script {
                    // Execute required unit tests in parallel
                    parallel (
                        master: {
                            node ('master') {
                                sh '/opt/gradle-2.7/bin/gradle -D test.single=TestExample1 test'
                            }
                        },
                        worker2: {
                            node ('worker_node2') {
                                sh '/opt/gradle-2.7/bin/gradle -D test.single=TestExample2 test'
                            }
                        }
                    )
                }
            }
        }
    }
}
########################################################
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Stash files after the build
                    stash name: 'buildArtifacts', includes: '**/*.jar', excludes: '**/test-*.jar'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // Unstash the files before running tests
                    unstash 'buildArtifacts'
                    
                    // Run your tests here
                    echo 'Running tests...'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    // Unstash the files before deployment
                    unstash 'buildArtifacts'
                    
                    // Deployment steps here
                    echo 'Deploying...'
                }
            }
        }
    }
}


Absolutely! The stash and unstash steps in a Jenkins pipeline are used to share files between different stages or nodes. Here’s how you can use them

#########################################################################


pipeline {
    agent any

    stages {
        stage('Source') {
            steps {
                git branch: 'test', url: 'git@diyv:repos/gradle-greetings'
                stash name: 'test-source', includes: 'build.gradle,src/test/'
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // Execute required unit tests in parallel
                    parallel (
                        master: {
                            node ('master') {
                                unstash 'test-sources'
                                sh '/opt/gradle-2.7/bin/gradle -D test.single=TestExample1 test'
                            }
                        },
                        worker2: {
                            node ('worker_node2') {
                                unstash 'test-sources'
                                sh '/opt/gradle-2.7/bin/gradle -D test.single=TestExample2 test'
                            }
                        }
                    )
                }
            }
        }
    }
}

Git stash Versus Jenkins stash

###############################################

pipeline {
    agent any

    stages {
        stage('Source') {
            steps {
                git branch: 'test', url: 'git@diyv:repos/gradle-greetings'
                stash name: 'ws-src', includes: 'build.gradle,src/test/'
            }
        }
        
        stage('Unit Test') {
            parallel {
                stage('Util unit tests') {
                    agent { label 'worker_node2' }
                    steps {
                        cleanWs()
                        unstash 'ws-src'
                        gbuild4 ':util:test'
                    }
                }
                stage('API unit tests set 1') {
                    agent { label 'worker_node3' }
                    steps {
                        // always run with a new workspace
                        cleanWs()
                        unstash 'ws-src'
                        gbuild4 '-D test.single=TestExample1* :api:test'
                    }
                }
                stage('API unit tests set 2') {
                    agent { label 'worker_node2' }
                    steps {
                        // always run with a new workspace
                        cleanWs()
                        unstash 'ws-src'
                        gbuild4 '-D test.single=TestExample2* :api:test'
                    }
                }
            }
        }
    }
}

############################################
pipeline {
    agent any

    stages {
        stage('Parallel') {
            steps {
                parallel (
                    'group1': {
                        timestamps {
                            catchError {
                                sleep 10
                                echo 'Completed group1 processing'
                            }
                        }
                    },
                    'group2': {
                        sleep 5
                        error 'Error in group2 processing'
                    },
                    failFast: true
                )
            }
        }
    }
}
#####################################################
pipeline {
    agent { label 'worker_node1' }

    stages {
        stage('Selection') {
            steps {
                script {
                    def responses = input message: 'Enter branch and select build type',
                    parameters: [
                        string(defaultValue: '', description: '', name: 'BRANCH_NAME'),
                        choice(choices: 'DEBUG\nRELEASE\nTEST', description: '', name: 'BUILD_TYPE')
                    ]
                }
            }
        }
        stage('Process') {
            steps {
                script {
                    if ((responses.BRANCH_NAME == 'master') && (responses.BUILD_TYPE == 'RELEASE')) {
                        echo "Kicking off production build\n"
                    } else {
                        echo "Selected branch: ${responses.BRANCH_NAME}, Build type: ${responses.BUILD_TYPE}"
                    }
                }
            }
        }
    }
}

The Selection stage prompts the user to enter a branch name and select a build type using the input step.

############################################################################

pipeline {
    agent any

    parameters {
        string(defaultValue: '', description: '', name: 'BRANCH_NAME')
        choice(choices: 'DEBUG\nRELEASE\nTEST', description: '', name: 'BUILD_TYPE')
    }

    stages {
        stage('process') {
            when {
                allOf {
                    expression { params.BRANCH_NAME == 'master' }
                    expression { params.BUILD_TYPE == 'RELEASE' }
                }
            }
            steps {
                echo "Kicking off production build\n"
            }
        }
    }
}

The parameters block defines two parameters: BRANCH_NAME (a string) and BUILD_TYPE (a choice with options 'DEBUG,' 'RELEASE,' and 'TEST').

The process stage contains a when block that checks if BRANCH_NAME is 'master' and BUILD_TYPE is 'RELEASE.'

If both conditions are met, it executes the steps within the stage, echoing "Kicking off production build."

#####################################################
pipeline {
    agent any

    stages {
        // Define your stages here
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test steps here
            }
        }
    } // end stages

    post {
        always {
            echo "Build stage complete"
        }
        failure {
            echo "Build failed"
            mail body: 'Build failed', subject: 'Build failed!',
            to: 'devops@company.com'
        }
        success {
            echo "Build succeeded"
            mail body: 'Build succeeded', subject: 'Build Succeeded',
            to: 'devops@company.com'
        }
    } // end post
} // end pipeline

always: Runs regardless of the build outcome.

failure: Executes if the build fails and sends an email notification.

success: Executes if the build succeeds and sends an email notification

####################################################################
pipeline {
    agent any

    stages {
        // Define your stages here
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test steps here
            }
        }
    } // end stages

    post {
        always {
            mail to: 'bcl@nclasters.org',
            subject: "Status of pipeline: ${currentBuild.fullDisplayName}",
            body: "${env.BUILD_URL} has result ${currentBuild.result}"
        }
    } // end post
}
######################################


pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test steps here
            }
        }
    }

    post {
        always {
            emailext (
                body: 'body goes here',
                recipientProviders: [
                    [$class: 'CulpritsRecipientProvider'],
                    [$class: 'DevelopersRecipientProvider'],
                    [$class: 'RequesterRecipientProvider'],
                    [$class: 'FailingTestSuspectsRecipientProvider'],
                    [$class: 'FirstFailingBuildSuspectsRecipientProvider'],
                    [$class: 'UpstreamComitterRecipientProvider']
                ],
                subject: 'subject goes here'
            )
        }
    }
}


Breakdown:
CulpritsRecipientProvider: Sends email to users who committed changes between the last successful build and the current build.

DevelopersRecipientProvider: Sends email to all users who made changes in the changeset.

RequesterRecipientProvider: Sends email to the user who initiated the build.

FailingTestSuspectsRecipientProvider: Sends email to users suspected of causing a unit test to begin failing.

FirstFailingBuildSuspectsRecipientProvider: Sends email to users suspected of causing the build to start failing.

UpstreamComitterRecipientProvider: Sends email to users who committed changes in upstream builds that triggered the current build.
##############################################################################

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test steps here
            }
        }
    }

    post {
        always {
            emailext (
                attachLog: true,
                compressLog: true,
                body: """
                    <p>EXECUTED: Job <b>'${env.JOB_NAME}:${env.BUILD_NUMBER})'</b></p>
                    <p>View console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"</p>
                    <p><i>(Build log is attached.)</i></p>
                """,
                recipientProviders: [
                    [$class: 'DevelopersRecipientProvider'],
                    [$class: 'RequesterRecipientProvider']
                ],
                replyTo: 'do-not-reply@company.com',
                subject: "Status: ${currentBuild.result ?: 'SUCCESS'} - Job '${env.JOB_NAME}:${env.BUILD_NUMBER}'",
                to: 'bcl@nclasters.org, Brent.Laster@domain.com'
            )
        }
    }
}
#####################################################

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test steps here
            }
        }
    }

    post {
        always {
            // Send email notifications
            emailext (
                attachLog: true,
                compressLog: true,
                body: """
                    <p>EXECUTED: Job <b>'${env.JOB_NAME}:${env.BUILD_NUMBER})'</b></p>
                    <p>View console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"</p>
                    <p><i>(Build log is attached.)</i></p>
                """,
                recipientProviders: [
                    [$class: 'DevelopersRecipientProvider'],
                    [$class: 'RequesterRecipientProvider']
                ],
                replyTo: 'do-not-reply@company.com',
                subject: "Status: ${currentBuild.result ?: 'SUCCESS'} - Job '${env.JOB_NAME}:${env.BUILD_NUMBER}'",
                to: 'bcl@nclasters.org, Brent.Laster@domain.com'
            )

            // Publish HTML report
            publishHTML(target: [
                allowMissing: false,
                alwaysLinkToLastBuild: false,
                keepAll: true,
                reportDir: 'api/build/reports/test',
                reportFiles: 'index.html',
                reportName: "API Unit Testing Results"
            ])
        }
    }
}
##############################################################################


pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
            }
        }
        stage('Test') {
            parallel {
                stage('Util unit tests') {
                    agent { label 'worker_node2' }
                    steps {
                        cleanWs()
                        unstash 'ws-src'
                        gbuild4 ':util:test'
                        stash name: 'util-reports', includes: 'util/build/reports/test/**'
                    }
                }
                stage('API unit tests set 1') {
                    agent { label 'worker_node3' }
                    steps {
                        cleanWs()
                        unstash 'ws-src'
                        gbuild4 '-D test.single=TestExample1* :api:test'
                        stash name: 'api-reports', includes: 'api/build/reports/test/**'
                    }
                }
                stage('API unit tests set 2') {
                    agent { label 'worker_node2' }
                    steps {
                        cleanWs()
                        unstash 'ws-src'
                        gbuild4 '-D test.single=TestExample2* :api:test'
                        stash name: 'api-reports', includes: 'api/build/reports/test/**', allowEmpty: true
                    }
                }
            }
        }
    }

    post {
        always {
            emailext (
                attachLog: true,
                compressLog: true,
                body: """
                    <p>EXECUTED: Job <b>'${env.JOB_NAME}:${env.BUILD_NUMBER})'</b></p>
                    <p>View console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"</p>
                    <p><i>(Build log is attached.)</i></p>
                """,
                recipientProviders: [
                    [$class: 'DevelopersRecipientProvider'],
                    [$class: 'RequesterRecipientProvider']
                ],
                replyTo: 'do-not-reply@company.com',
                subject: "Status: ${currentBuild.result ?: 'SUCCESS'} - Job '${env.JOB_NAME}:${env.BUILD_NUMBER}'",
                to: 'bcl@nclasters.org, Brent.Laster@domain.com'
            )

            finally {
                // Unstash and publish API unit testing results
                unstash 'api-reports'
                publishHTML(target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'api/build/reports/test',
                    reportFiles: 'index.html',
                    reportName: "API Unit Testing Results"
                ])
                
                // Unstash and publish Util unit testing results
                unstash 'util-reports'
                publishHTML(target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'util/build/reports/test',
                    reportFiles: 'index.html',
                    reportName: "Util Unit Testing Results"
                ])
            }
        }
    }
}
