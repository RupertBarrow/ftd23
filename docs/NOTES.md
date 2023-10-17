# 1. INITIALISATION

## 1. Create a dev org which will mimic production and hold the DevHub ("production")

- enable Dev Hub
- enable Unlocked Packages and Second-Generation Managed Packages
- install the "Package Visualizer" package from the AppExchange

## 2. Create a dev org which will mimic a sandbox ("sandbox")

## 3. Create a new Github repository ("ftd23-talk")

- checkout locally
- create an SFDX project :

```
sf project generate -name "ftd23-packaging"
```

- make your first commit in Github

## 4. Auth into the DevHub ("production") and "sandbox" orgs and set this as default

- authenticate with the DevHub ("production") org :

```
sf org login web --alias production --set-default-dev-hub
```

- authenticate with the "sandbox" org and set it as our default org :

```
sf org login web --alias sandbox --set-default
```

## 5. Best practice : create a Github issue and a branch to work on

# 2. CREATE A PACKAGE

## Create an unlocked, org-dependent package (with no namespace)

```
sf package create --name "main-package" --path "main-package" --package-type Unlocked --org-dependent --target-dev-hub production --no-namespace
```

=> Screenshots of Salesforce : Package Visualizer

- 01 the package has been created
- 02 it has no package versions
  => Screenshots of VS Code :
- 03 sfdx-project.json has been updated

## In the Salesforce "sandbox" org : create a new custom field

- "FTD description" custom field on the "Account" object

## In VS Code : retrieve the new custom field

- using the Salesforce Org Browser
- right

## In VS Code : move the new custom field to the "main package" folder

## In VS Code : create a package version

```
sf package version create -p "main-package" -x
```

=> Screenshots of Salesforce : Package Visualizer

- 04 the package version has been created
- 04b package version details

## Install the package in the target org

- by command-line :

```
sf package install -p "main-package@0.1.0-1" -o production
```

- by URL :
  https://ftd23-packages-sandbox-dev-ed.develop.my.salesforce.com/packagingSetupUI/ipLanding.app?apvId=04t060000002Zp9AAE

=> Screenshot of Salesforce :

- 05 New package version installed - installed packages.png
- 06 Custom field in installed package version in production
