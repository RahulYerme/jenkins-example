pipeline {
    agent any
     tools { 
        maven 'Apache Maven 3.6.3' 
        
    }

    stages {
        stage ('Compile Stage') {

            steps {
                script{
                    sh 'mvn clean package'
                }
            }
        }

        stage ('Code sign stage') {
            steps {
                script{
                 sh '''#! /bin/bash
                 jarsigner   -keystore NONE -storetype AzureKeyVault \
                 -signedjar signerjar.jar jenkins-example-1.0-SNAPSHOT.jar TestSSC \
                 -verbose  -storepass "" \
                 -providerName AzureKeyVault \
                 -providerClass org.azure.security.keyvault.jca.KeyVaultJcaProvider\
                 -J-Dazure.keyvault.uri=https://poc-data-key-vault.vault.azure.net \
                 -J-Dazure.keyvault.tenant-id=8c3dad1d-b6bc-4f8b-939b-8263372eced6 \
                 -J-Dazure.keyvault.client-id=a2220dff-d6a3-4728-99a7-6083cdaf8937 \
                 -J-Dazure.keyvault.client-secret=GDS8Q~X5.WjXNp0f1Y.-5SuROlhX5KGHSncXcdiK 
                 '''
                }
            }
        }
    }
}
