pipeline {
    agent any
    stages {

        stage('Check Parameter') {
            steps{
                script{
                     sh "echo ${VERSION}"
                     assert '' != params.VERSION :'Invalid parameter WORK_HOME'
                     assert '' != params.CONTAINER_NAME :'Invalid parameter CONTAINER_NAME'
                     assert '' != params.IP :'Invalid parameter IP'
                     assert '' != params.PORT :'Invalid parameter PORT'
                     assert '' != params.MIRROR_IMAGE :'Invalid parameter MIRROR_IMAGE'
                     assert '' != params.RESTART :'Invalid parameter RESTART'
                     assert '' != params.MAP :'Invalid parameter MAP'
                }
           }
       }


       stage('Deploy') {
           steps{
               script{

                    var = ${MAP}.replaceAll(" ", " \\-e " )
                    
                     sh '''
                     // ssh root@10.15.46.184 "docker inspect --format={{.ID}}  param.CONTAINER_NAME 2> /dev/null; if( $? -eq 0) then echo 123 ;fi;sleep 10;"
                     // ssh root@10.15.46.184 'echo -e "docker run --name param.CONTAINER_NAME var -v param.CONTAINER_TIME --restart param.RESTART-p param.PORT -d param.MIRROR_IMAGEparam.CONTAINER_NAME:param.VERSION" '
                     '''

           

               }
           }
       }


    }

}


