pipeline {
    agent any
    stages {

        stage('Check Parameter') {
            steps{
                script{
                     assert '' != ${VERSION} :'Invalid parameter WORK_HOME'
                     assert '' != ${CONTAINER_NAME} :'Invalid parameter CONTAINER_NAME'
                     assert '' != ${IP} :'Invalid parameter IP'
                     assert '' != ${PORT} :'Invalid parameter PORT'
                     assert '' != ${MIRROR_IMAGE} :'Invalid parameter MIRROR_IMAGE'
                     assert '' != ${RESTART} :'Invalid parameter RESTART'
                     assert '' != ${MAP} :'Invalid parameter MAP'
                }
           }
       }


       stage('Deploy') {
           steps{
               script{

                    var = ${MAP}.replaceAll(" ", " \\-e " )
                     sh '''
                     ssh root@10.15.46.184 'echo -e "docker inspect --format={{.ID}}  ${CONTAINER_NAME}  2> /dev/null; if( $? -eq 0) then echo 123 ;fi;sleep 10;"'
                     ssh root@10.15.46.184 'echo -e "docker run --name ${CONTAINER_NAME} var -v ${CONTAINER_TIME} --restart ${RESTART} -p ${PORT} -d ${MIRROR_IMAGE}${CONTAINER_NAME}:${VERSION}" '
                     '''
                    

           

               }
           }
       }


    }

}


