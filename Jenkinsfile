pipeline {
    agent any

    environment {
        CUSTOM_WORKSPACE = "/Users/yagmar/Documents/pipeline"
    }

    stages {
        stage('Préparation du dossier') {
            steps {
                script {
                    echo '📂 Création du dossier de travail'
                    sh "mkdir -p ${env.CUSTOM_WORKSPACE}"
                    echo "✅ Dossier de travail : ${env.CUSTOM_WORKSPACE}"
                }
            }
        }

        stage('Clonage du dépôt') {
            steps {
                script {
                    dir(env.CUSTOM_WORKSPACE) {
                        checkout scm
                    }
                    echo "✅ Code cloné dans : ${env.CUSTOM_WORKSPACE}"
                }
            }
        }

        stage('Créer un fichier') {
            steps {
                script {
                    dir(env.CUSTOM_WORKSPACE) {
                        sh 'touch mon_fichier.txt'
                        echo '✅ Fichier créé : mon_fichier.txt'
                    }
                }
            }
        }

        stage('Écrire dans le fichier') {
            steps {
                script {
                    dir(env.CUSTOM_WORKSPACE) {
                        sh 'echo "Ceci est un test avec Jenkins." > mon_fichier.txt'
                        echo '✅ Texte ajouté dans mon_fichier.txt'
                    }
                }
            }
        }

        stage('Vérifier le contenu du fichier') {
            steps {
                script {
                    dir(env.CUSTOM_WORKSPACE) {
                        sh 'cat mon_fichier.txt'
                        sh 'pwd'
                    }
                }
            }
        }
    }

    post {
        success {
            echo '🎉 SUCCESS : La pipeline a été exécutée avec succès ! ✅'
        }
        failure {
            echo '❌ Échec : Un problème est survenu pendant l’exécution de la pipeline.'
        }
    }
}
