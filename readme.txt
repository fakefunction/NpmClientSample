

see for more info :
 https://docs.microsoft.com/en-us/azure/devops/artifacts/npm/npmrc?view=azure-devops&tabs=windows

steps :

prerequisite : you need two .npmrc files
   - One .npmrc should live at the root of your git repo adjacent to your project's package.json
   - One in your %USERPROFILE%\.npmrc This .npmrc should contain credentials for all of the registries that you need to connect to. 
   - The NPM client will look at your project's .npmrc, discover the registry, and fetch matching credentials from 

1. Add the following to you package.json inside script 
    "refreshVSToken": "vsts-npm-auth -config .npmrc"

2. create a new file .npmrc in yhe root of your git repo adjacent to your project's package.json

3. add this to the .npmrc file 
   registry=https://pkgs.dev.azure.com/CalculatorLibDev/_packaging/CalculatorLib.Common/npm/registry/
   always-auth=true
4. run command
   npm install -g vsts-npm-auth --registry https://registry.npmjs.com --always-auth false

5. Then run this ( will prompt you fro credentials and update your %USERPROFILE%\.npmrc )
   vsts-npm-auth -config .npmrc

5b. If you dont want to login (may be you dont have an account in to the azure profile devops) you 
    can just copy the  credentials from your azure devops directly into your user %USERPROFILE%\.npmrc manually
    link : https://dev.azure.com/CalculatorLibDev/Lib/_packaging?_a=package&feed=CalculatorLib.Common&package=calculatorlib.jslib&protocolType=Npm&version=1.0.0

6. Done!


