# Test app

Test app deployed on k8s with helm

## Tested on:
* kubernetes running in digital ocean - `v1.21.5`
* helm `3.7.2`

Service is listening on nodePort `30012` (can be changed in `chart/values.yaml`)

## Assumptions:
* I ignored building the container to save time on setting up the container registry (it's only build, tag and push)
* using build in secrets store in k8s
* secret is stored in git only for example purpose. Storing any secrets in git is bad idea
* chart is missing few variables as they are not required for the example

## CI:
* GitHub Actions - easiest to use in this case
    - security scan with anchore (simplified for this example purpose, it should scan container created from the CI rather than image directly from the Docker Hub)
    - linting with superliner - with default settings that should be adjusted based on the preferences
