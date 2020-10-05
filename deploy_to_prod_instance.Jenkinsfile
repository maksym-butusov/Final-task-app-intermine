node {
    
    stage('Deploy to PROD instance') {
        script {
            // Define Variable
             def USER_INPUT = input(
                    message: 'Please approve deployment and choose what deploy you need to do?',
                    parameters: [
                            [$class: 'ChoiceParameterDefinition',
                             choices: ['Deploy containers firts time','Update containers'].join('\n'),
                             name: 'input',
                             description: 'Menu - select box option']
                    ])

            echo "${USER_INPUT}"

            if( "${USER_INPUT}" == "Deploy containers firts time"){
                sshagent (credentials: ['stage']) {
                sh 'ssh -o StrictHostKeyChecking=no -l inception 35.228.159.105 "git clone https://github.com/maksym-butusov/docker-intermine-gradle && cd docker-intermine-gradle && ./mkdatadirs.sh dockerhub.docker-compose.yml && sudo chmod -R 777 data/solr && docker-compose -f dockerhub.docker-compose.yml up -d"'
                }
            } else {
                sshagent (credentials: ['stage']) {
                sh 'ssh -o StrictHostKeyChecking=no -l inception 35.228.159.105 "cd docker-intermine-gradle && docker-compose -f dockerhub.docker-compose.yml down && docker system prune -a -f && cd .. && sudo rm -rf docker-intermine-gradle/ && git clone https://github.com/maksym-butusov/docker-intermine-gradle && cd docker-intermine-gradle && ./mkdatadirs.sh dockerhub.docker-compose.yml && sudo chmod -R 777 data/solr && docker-compose -f dockerhub.docker-compose.yml up -d"'
                }
            }
        }
    }
}
