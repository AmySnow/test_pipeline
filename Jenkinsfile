pipeline {
    agent any
    stages {

        stage('Check paramseter') {
            steps{
                script{
                     assert '' != params.VERSION :'Invalid paramseter WORK_HOME'
                     assert '' != params.CONTAINER_NAME :'Invalid paramseter CONTAINER_NAME'
                     assert '' != params.IP :'Invalid paramseter IP'
                     assert '' != params.PORT :'Invalid paramseter PORT'
                     assert '' != params.MIRROR_IMAGE :'Invalid paramseter MIRROR_IMAGE'
                     assert '' != params.RESTART :'Invalid paramseter RESTART'
                     assert '' != params.MAP :'Invalid paramseter MAP'
                }
           }
       }


       stage('Deploy') {
           steps{
               script{
                   def VarMap =  MAP.split(",")
                   def VarM = ''
                   for(int i=0; i<VarMap.size(); i++ ) {
                        def VarM = VarM + '-e' + VarMap[i]
                   }
                   println(VarM);

               }
           }
       }


    }

}


