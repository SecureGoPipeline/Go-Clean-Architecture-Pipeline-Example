# Secure pipeline example
Example codebase from: https://github.com/AleksK1NG/Go-Clean-Architecture-REST-API

# Choices
During a pipeline analysis, a couple of security controls were recommended. Following that advice the following security controls were implemented:
* Static code scanning: [SonarCloud](https://www.sonarsource.com/products/sonarcloud/) 
* Dynamic code scanning: [StackHawk](https://www.stackhawk.com/)
* Dependency scanning: [Snyk](https://snyk.io/product/open-source-security-management/)
* Container scanning: [Snyk](https://snyk.io/product/container-vulnerability-management/)

### Design choices
During the development of the example pipeline, the choice was made to focus on the master branch. When using multiple development branches it would be recommended to limit the execution of certain security controls to retain instant feedback. For example, a dynamic code scan should be run on features that are complete. In this case, full security checks would be run when merging into the master.

This pipeline has been configured to prevent the merging of high vulnerabilities. This could be configured further.

# Result
When a vulnerability is detected it is stored in the code analysis tab within GitHub. Should say vulnerability be deemed as 'high' the build shall fail and deployment is prevented.

# Recommendation
The following security controls proved to be of immediate benefit.
* Static code scanning: [SonarCloud](https://www.sonarsource.com/products/sonarcloud/) 
* Dependency scanning: [Snyk](https://snyk.io/product/open-source-security-management/)

Dynamic code scanning has its benefits but most of these mostly apply to an API that follows the [OpenAPI specification](https://swagger.io/resources/open-api/) this allows the tool to scan the available endpoints for unexpected responses or vulnerable input.

Container scanning only proves useful the docker file uses a distribution. Should a distroless static or scratch base image be used, there would be nothing for the container scanning tool to scan and this step could be ignored.
