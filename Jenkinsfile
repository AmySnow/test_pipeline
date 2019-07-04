pipeline {
    agent any
    stages {

        stage('Check paramseter') {
            steps{
                script{
                     sh "echo ${VERSION}"

                     assert '' != env.VERSION :'Invalid paramseter WORK_HOME'
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
                     sh '''
                     
                     ssh root@10.15.46.184 "docker inspect --format={{.ID}}  params.CONTAINER_NAME 2> /dev/null; if( $? -eq 0) then echo 123 ;fi;sleep 10;"
                      ssh root@10.15.46.184 'echo -e "docker run --name params.CONTAINER_NAME var -v params.CONTAINER_TIME --restart params.RESTART-p params.PORT -d params.MIRROR_IMAGEparams.CONTAINER_NAME:params.VERSION" '
                     '''

           

               }
           }
       }


    }

}


