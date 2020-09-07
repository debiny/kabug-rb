pipeline{
    agent {
        docker{
            image "ruby"
        }
    }
    
    stages{
        stage('Build'){
            steps {echo "Resolvendo dependecias"
            sh 'bundle install'
                
            }
            
        }
        stage('Test'){
            steps {
                echo "Executando testes"
                sh 'bundle exec cucumber -p ci'
        }
    }
        stage('UAT'){
            steps {
                echo "Aguardando teste manual"
                input(message: "Vamos para produção? ok: Yes")
            }
        }
        stage('Prod'){
            steps {
                echo "Testes finalizados e projeto pronto para produção :) "
            }
        }
    }
}
