Azure Data lake with V1 is going to Expire, we have to use Datalake with V2, which is nothing but a storage account with V2,
we can directly upload the files to the storage account using below powershell 



trigger:
- none

pool:
  vmImage: 'windows-latest'

stages:
  - stage: Test
    displayName: Tst
    jobs:
      - deployment: Deploy
        displayName: Deploy Databricks and Data Lake files

        strategy:
          runOnce:
            deploy:
              steps:
              - checkout: self              
              - task: AzureFileCopy@4
                inputs:
                  sourcePath: /
                  azureSubscription: 
                  destination: # Options: azureBlob, azureVMs
                  storage: 
                   containerName: # Required when destination == AzureBlob
