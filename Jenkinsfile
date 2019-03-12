pipeline    {
    
    parameters {
        string(name: 'ResourseGroup', defaultValue: 'OpenshiftGroupTest', description: "Azure's resours group")
        string(name: 'Name VM machine', defaultValue: 'myOpenshiftVM', description: 'Name of VM machine')
        string(name: 'AdminUserName', defaultValue: 'azureuser', description: 'Admin User Name for VM machine')
    }
    
    agent none

    stages {

            echo "My client id is $AZURE_CLIENT_ID"
            echo "My client secret is $AZURE_CLIENT_SECRET"
            echo "My tenant id is $AZURE_TENANT_ID"
            echo "My subscription id is $AZURE_SUBSCRIPTION_ID"
        
        // With defaults, which will read specified service principal into four predefined 
        // environment variables: AZURE_SUBSCRIPTION_ID, AZURE_CLIENT_ID, AZURE_CLIENT_SECRET, AZURE_TENANT_ID. 
        // Sample pipeline code:
        withCredentials([azureServicePrincipal('credentials_id')]) {
            sh 'az login --service-principal -u $AZURE_CLIENT_ID -p $AZURE_CLIENT_SECRET -t $AZURE_TENANT_ID'
        }

        //With custom name, where you can control the names of the variables. Sample pipeline code:
        withCredentials([azureServicePrincipal(credentialsId: 'credentials_id',
                                    subscriptionIdVariable: 'SUBS_ID',
                                    clientIdVariable: 'CLIENT_ID',
                                    clientSecretVariable: 'CLIENT_SECRET',
                                    tenantIdVariable: 'TENANT_ID')]) {
            sh 'az login --service-principal -u $CLIENT_ID -p $CLIENT_SECRET -t $TENANT_ID'
}



    }