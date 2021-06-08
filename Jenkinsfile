//Pipeline declarativo siempre se empieza con pipeline{}
pipeline {
    
    //Declaramos el nodo o agente que ejecutara las tareas, en este caso cualquiera disponible
  agent {
    node{
      label 'principal'
    }
  }
  
  options{
    //ficheros de log
    buildDiscarder logRotator(
      daysToKeepStr: '15', 
      numToKeepStr. '10'
    )
  }
    
    //definicion de fases
    stages{
        
        //primera stage
        stage('Cleanup Workspace'){
            //definimos los pasos de cada stage
            steps{
                
                cleanWs()
              echo 'Eliminado ws para job';
            }
        }
        
        //primera stage
        stage('Code Checkout'){
            //definimos los pasos de cada stage
            steps{
                
                checkout(
              $class: 'GitSCM',
              branches: [[name: '*/main']],
              userRemoteConfigs: [[url: 'http://github.com/spring-projects/spring-petclinic.git']]
                  )
            }
        }
       stage('Unit test'){
            //definimos los pasos de cada stage
           when{
               branch 'testing'
           }
            steps{
                echo 'unit testint';
            }
        }
        stage('Code Analysis'){
            //definimos los pasos de cada stage
            when{
                branch 'developer'
            }
            steps{
                echo 'analysis';
            }
        }
        
    }
    
    
}
