# Test app

Test app for k8s with deployed with helm

## Tested on
* kubernetes running in digital ocean - `v1.21.5`
* helm `3.7.2`

Service is listening on nodePort `30012` (can be changed in `chart/values.yaml`)

## Assumptions
* I ignored building the container to save time on setting up the container registry (it's only build, tag and push)
* using build in secrets store in k8s
* secret is stored in git only for example purpose. Storing any secrets in git is bad idea
* chart is missing few variables as they are not required for the example
* will be deployed in `default` namespace

## CI
* GitHub Actions - easiest to use in this case
  - security scan with `anchore`
    - simplified for this example purpose, not user friendly as there is no output why the workflow failed
    - it should scan container created from the CI rather than image directly from the Docker Hub
    - ignored the results from security scan as official image is waiting for being patched ;) 
  - linting with `superliner`
    - with default settings that should be adjusted based on the preferences

## Deployment:
* manually with helm by running `helm install [NAME] chart`
  - you need to have your `kubectl` connected to the k8s cluster
* pipeline
  - any CD tool allowing to run `helm`
  - GitOps tools like ArgoCD
