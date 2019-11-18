pipeline {
    agent any
    stages {
        stage('pulling from git') {
            steps {
               git 'https://github.com/kohbah/vsphere.git'
            }
        }     
        stage('creating_VM') {
            steps {
               vSphere buildStep: [$class: 'Clone', clone: 'node1', cluster: 'Compute-Cluster-01', customizationSpec: '', datastore: '', folder: '', linkedClone: false, powerOn: true, resourcePool: '', sourceName: 'ubuntu18', timeoutInSeconds: 60], serverName: 'vcenter'
            }
        }        
        
      }
   }
    
