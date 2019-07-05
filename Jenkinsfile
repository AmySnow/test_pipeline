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

                     def varMap = MAP.replaceAll(" ", " \\-e " )
                     sh """ssh root@10.15.46.184 "docker inspect --format={{.ID}}  ${CONTAINER_NAME}  2> /dev/null; if( $? -eq 0) then docker rm  -f  ${CONTAINER_NAME}; fi; sleep 10;" """
                     sh """ssh root@10.15.46.184 "docker run --name ${CONTAINER_NAME} -e ${varMap} -v ${CONTAINER_TIME} --restart ${RESTART} -p ${PORT} -d ${MIRROR_IMAGE}${CONTAINER_NAME}:${VERSION}" """

               }
           }
       }


    }

}


