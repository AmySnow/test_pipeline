pipeline {
    agent any
    stages {

        stage('Check Parameter') {
            steps{
                script{
                    sh  "echo params.VERSION"
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

                    var = params.MAP.replaceAll(" ", " \\-e " )
                     sh '''
                     ssh root@10.15.46.184 "docker inspect --format={{.ID}}  params.CONTAINER_NAME  2> /dev/null; if( $? -eq 0) then echo 123 ;fi;sleep 10;"
                     ssh root@10.15.46.184 'echo -e "docker run --name params.CONTAINER_NAME var -v params.CONTAINER_TIME --restart params.RESTART -p params.PORT -d params.MIRROR_IMAGE params.CONTAINER_NAME:params.VERSION" '
                     '''
                    

           

               }
           }
       }


    }

}


