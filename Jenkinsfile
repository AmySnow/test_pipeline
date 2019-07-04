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

                    echo '123455'

               }
           }
       }


    }

}


