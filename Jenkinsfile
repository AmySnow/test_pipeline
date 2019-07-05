pipeline {
    agent any
    stages {

        stage('Check paramseter') {
            steps{
                script{
                     sh "echo {params.VERSION}"
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
                     varMap = ${MAP}.replaceAll(" ", " \\-e " )
                     echo ${varMap}
                     // ssh root@10.15.46.184 "docker inspect --format={{.ID}}  ${CONTAINER_NAME}  2> /dev/null; if( $? -eq 0) then echo 123 ;fi;sleep 10;"
                     sh 'ssh root@10.15.46.184 echo -e "docker run --name ${CONTAINER_NAME} ${varMap} -v ${CONTAINER_TIME} --restart ${RESTART} -p ${PORT} -d ${MIRROR_IMAGE}${CONTAINER_NAME}:${VERSION}" '

               }
           }
       }


    }

}


