# Containers 2.0 Openhack

<!-- 
Guidelines on README format: https://review.docs.microsoft.com/help/onboard/admin/samples/concepts/readme-template?branch=master

Guidance on onboarding samples to docs.microsoft.com/samples: https://review.docs.microsoft.com/help/onboard/admin/samples/process/onboarding?branch=master

Taxonomies for products and languages: https://review.docs.microsoft.com/new-hope/information-architecture/metadata/taxonomies?branch=master
-->

This repo houses the source code and dockerfiles for the Containers OpenHack event.

The application used for this event is a heavily modified and recreated version of the original [My Driving application](https://github.com/Azure-Samples/MyDriving).

## Contents

| File/folder       | Description                                |
|-------------------|--------------------------------------------|
| `.devcontainer`   | VS Code [development container](https://code.visualstudio.com/docs/remote/containers) with useful utils (Azure CLI, Kubectl, Helm, etc.)   |
| `dockerfiles`     | Dockerfiles for source code                |
| `src`             | Sample source code for POI, Trips, User (Java), UserProfile (Node.JS), and TripViewer                     |
| `.gitignore`      | Define what to ignore at commit time.      |
| `CODE_OF_CONDUCT.md` | Code of conduct.                        |
| `LICENSE`         | The license for the sample.                |

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.


```dockerfile
docker run --network bridge -e SQLFQDN=sqlserveracs2871.database.windows.net -e SQLUSER=sqladminaCs2871 -e SQLPASS=OpenHackTeam5 -e SQLDB=mydrivingDB openhack/data-load:v1
```

sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=Password1" \
   -p 1433:1433 --name sql -h sql \
   -d \
   mcr.microsoft.com/mssql/server:2017-latest

   docker run --network bridge -e SQLFQDN=172.17.0.3 -e SQLUSER=SA -e SQLPASS=Password1 -e SQLDB=mydrivingDB openhack/data-load:v1

   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P 'Password1'
   1> select name from sys.databases
   2> GO
1> SELECT * FROM Trips
2> GO

docker run -d -p 8080:80 --name poi -e "SQL_PASSWORD=Password1" -e "SQL_SERVER=tcp:172.17.0.3,1433" -e "ASPNETCORE_ENVIRONMENT=Local" tripinsights/poi:1.0

docker build -f /workspaces/containers_artifacts/dockerfiles/Dockerfile_4 -t tripinsights/trips:1.0 .

az acr build --image  tripinsights/poi:1.0\
  --registry registryacs2871 \
  --file /workspaces/containers_artifacts/dockerfiles/Dockerfile_3 . 

  az acr login --name registryacs2871

  docker tag tripinsights/trips:1.0 registryacs2871.azurecr.io/tripinsights-trips:1.0

  docker push registryacs2871.azurecr.io/tripinsights-trips:1.0

  az aks get-credentials --resource-group teamResources --name TripviewerCluster
    az aks get-credentials --resource-group teamResources --name tripinsights-04 --overwrite-existing