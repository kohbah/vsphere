pipeline {
    agent any
    stages {
        stage('pulling from git') {
            steps {
               git 'https://github.com/kohbah/vsphere.git'
            }
        }     
        stage('deploying vm from ubuntu template') {
            steps {
              vSphere buildStep: [$class: 'Deploy', clone: 'node1', cluster: 'Compute-Cluster-01', datastore: '', folder: '', linkedClone: false, powerOn: false, resourcePool: '', template: 'ubuntu', timeoutInSeconds: 60], serverName: 'vcenter'
            }
        }   
        stage('reconfigureing vm to 2 cpu and 4 cores ') {
            steps {
               vSphere buildStep: [$class: 'Reconfigure', reconfigureSteps: [[$class: 'ReconfigureCpu', coresPerSocket: '4', cpuCores: '2']], vm: 'node1'], serverName: 'vcenter'
            }
        }  
        stage('creating memory to 2 GB') {
            steps {
             vSphere buildStep: [$class: 'Reconfigure', reconfigureSteps: [[$class: 'ReconfigureMemory', memorySize: '2048']], vm: 'node1'], serverName: 'vcenter'
            }
        }       
        stage(' powering on vm') {
            steps {
               vSphere buildStep: [$class: 'PowerOn', timeoutInSeconds: 180, vm: 'node1'], serverName: 'vcenter'
            }
        }    
      }
   }
    
