# 1. Create a dev org which will mimic production and hold the DevHub ("production")

- enable Dev Hub

# 2. Create a dev org which will mimic a sandbox ("sandbox")

# 3. Create a new Github repository ("ftd23-talk")

- checkout locally
- create an SFDX project :

```
sf project generate -name "ftd23-packaging"
```
- first commit to Github

- authenticate with the DevHub ("production") org :
```
sf org login web --alias production --set-default-dev-hub
```
