In this step, you create a bot application service which sets the deployment stage for the bot. You use an ARM template, a new service plan and a new resource group.

From the resulting JSON output, copy the numeric value of the **id** field to use as the value for the **registration subscription id** in the next step.

> [!NOTE]
> This step can take a few minutes to complete.

```cmd
az deployment create --template-file "<path-to-template-with-new-rg.json" --location <region-location-name> --parameters appId="<app-id-from-previous-step>" appSecret="<password-from-previous-step>" botId="<id or bot-app-service-name>" botSku=F0 newAppServicePlanName="<new-service-plan-name>" newWebAppName="<bot-app-service-name>" groupName="<new-group-name>" groupLocation="<region-location-name>" newAppServicePlanLocation="<region-location-name>" --name "<bot-app-service-name>"
```

| Option   | Description |
|:---------|:------------|
| name | The display name to use for your bot channels registration. Default is the value of the `botId` parameter.|
| template-file | The path to the ARM template. Usually, the `template-with-new-rg.json` file is provided in the `deploymentTemplates` folder of the bot project. This is a path to an existing template file. It can be an absolute path, or relative to the current directory. All bot templates generate ARM template files.|
| location |Location. Values from: `az account list-locations`. You can configure the default location using `az configure --defaults location=<location>`. |
| parameters | Deployment parameters, provided as a list of key=value pairs. Enter the following parameter values:

- `appId` - The *app id* value generated by the previous step.
- `appSecret` - The password you provided in the previous step.
- `botId` - A name for the  Bot Channels Registration resource to create. It must be globally unique. It is used as the immutable bot ID. It is also used as the default display name, which is mutable.
- `botSku` - The pricing tier; it can be F0 (Free) or S1 (Standard).
- `newAppServicePlanName` - The name of the new application service plan.
- `newWebAppName` - A name for the bot application service.
- `groupName` - A name for the new resource group.
- `groupLocation` - The location of the Azure resource group.
- `newAppServicePlanLocation` - The location of the application service plan.