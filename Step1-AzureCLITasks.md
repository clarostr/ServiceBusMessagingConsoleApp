On Azure Cloud Shell with Bash profile set Azure CLI variables that will be referred to while using the commands.
```azurecli
resourceGroupName=MyServiceBusAppRG

myLocation=westeurope  # In case needed get other locations with the following CLI command
az account list-locations # Will list all available locations
myNameSpaceName=ServiceBusNameSpace$RANDOM # Last part adds a randomized number to escape from potential duplicates.
serviceBusQueueName=MyServiceBusAppQueue
# Let's create a resource group to store resources
az group create --name $resourceGroupName --location $myLocation
# Let's create the namespace
az servicebus namespace create \
    --resource-group $resourceGroupName \
    --name $myNameSpaceName \
    --location $myLocation
# Let's create the service bus queue
az servicebus queue create --resource-group $resourceGroupName \
    --namespace-name $myNameSpaceName \
    --name $serviceBusQueueName
```
