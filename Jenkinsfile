pipeline {
    agent any

    stages {
        stage('Créer un dossier') {
            steps {
                script {
                    sh 'mkdir -p mon_dossier'
                    echo '✅ Dossier créé : mon_dossier'
                }
            }
        }

        stage('Créer un fichier') {
            steps {
                script {
                    sh 'touch mon_dossier/mon_fichier.txt'
                    echo '✅ Fichier créé : mon_fichier.txt'
                }
            }
        }

        stage('Écrire dans le fichier') {
            steps {
                script {
                    sh 'echo "Ceci est un test avec Jenkins." > mon_dossier/mon_fichier.txt'
                    echo '✅ Texte ajouté dans mon_fichier.txt'
                }
            }
        }

        stage('Vérifier le contenu du fichier') {
            steps {
                script {
                    sh 'cat mon_dossier/mon_fichier.txt'
                    sh 'pwd'
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