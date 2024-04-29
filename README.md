# Yaml-scrpiting

- YAML stands YAML aint langauge
- It is a data serialization langauge   like json,xml
- It is simple,text based,human readable langugae
- It is not a programming langauge it is used for configuration files
- It supports arrys,list,dict
- the file extesnsion is .yaml and .yml
**What is data serialization?**
 - It is the process of converting data to format that easly stored/recovered
**YAML Structure**
 - Everything in yaml is key-value pair `key:value`
 - The keys are always strings
 - The yaml file start with ---
 - Whitespaces is part of yamal scrpiting
 - Newline indicates the end of the field
 - Idendataion levels can be one or more spaces
-------------------------Jenkins pipeline Tutorial------------------
   **pipeline:** It is like a blue print how our software will build and delivered.
   **Agent**:  It specifies where our blueprint will excuted.
   **Tools**:Need tools to build something like maven...
   **Options**: We can set our preference like how many previous version we need
   **Environment**: Setting environement
   **Stages**:
   --------------------------Yaml code-------------------
   agent {
    node {
        label 'SLAVE01'
    }
}
**Explanation:**
agent:This keyword indicates the begining of the block where we can define the execution  environment of our pipeline
node: Itspecifies the pipeline should run on specific node in jenkins environment. It can be master or worker node
label'SLAVE01' : It indicateds the pipeline should run on the slave01 node
--------------------------------------------------------
 tools {
        maven 'maven3'
    }
    options {
        buildDiscarder logRotator(
            daysToKeepStr: '15',
            numToKeepStr: '10'
        ) 
    }
**Explanation:**
Tools: Here we are creating toolkit before starting project. Here we are using maven tool and version3
buildDiscarder: This is like a setting a rule for how jenkins handle old builds 
logrotator: This is a specific method jenkins used to handle old builds. 
daystokeepstr15: Jenkins to keep build 15 days after 15 days it will automatically delete any builds
numtokeepsrt10: This tells jenkins to keep 10 builds at a time. after 10 builds it will older one and it creates new builds
--------------------------------------------------
environment {
        APP_NAME = "DCUBE_APP",
        APP_ENV = "DEV"
    }
   Explanatination:  
   environment: It is like a preparing workspace before starting the project and project name is ="DCUBE_APP" and env is dev
   ---------------------------------------------------------
   stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace for ${APP_NAME}"
                """
            }
        }
     Explanation:
      Stage(cleanup): It is cleaning workspace before doing the project
      cleanWs(): It clean the workspace
    ----------------------------------------------------
    stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/master']],
                    userRemoteConfigs: [[url: 'https://github.com/spring-projects/spring-petclinic.git']]
                ])
            }
        }
        stage('Code Build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true'
            }
        }
        stage('Printing All Global Variables') {
            steps {
                sh """
                env
                """
            }
        }
    }
}
Explanatation:
code checkout: here we are fectching code from gitrepo

   


