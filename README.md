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
buildDiscarder logRotator(...):


