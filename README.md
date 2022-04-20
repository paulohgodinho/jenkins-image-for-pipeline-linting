# jenkins-image-for-pipeline-linting
Jenkins docker image for usage with Jenkins Pipeline Linter Plugin for Visual Studio Code and IntelliJ IDEs.

## Visual Studio Code Usage
Pull the image from Dockerhub using:
```
docker pull paulohgodinho/jenkins-for-pipeline-linting
```

Run the container with the 8080 port exposed tot he host system
```
docker run -p 8080:8080 paulohgodinho/jenkins-for-pipeline-linting
```

Install the Jenkins Pipeline Linter Connect plugin for Visual Studio Code

![img](./readme-assets/vs-code-plugin.png)

Go to the extension settings

![img](./readme-assets/extension-settings.png)

Input the running Jenkins container URL with port and with the provided path

![img](./readme-assets/url-setup.png)

Run the linter by pressing *CTRL+SHIFT+P* and searchign for *Validate Jenkinsfile*

![img](./readme-assets/run-pallete.png)

## Validanting manualy
You can use Bash and Powershell to manually verify your Pipeline
Bash:
```
curl -F "jenkinsfile=< mypipeline.jenkinsfile" http://localhost:8080/pipeline-model-converter/validate
```
Powershell:
```
Invoke-RestMethod -Method Post -Body "jenkinsfile=$(Get-Content .\main.jenkinsfile -raw)" -Uri http://localhost:8080/pipeline-model-converter/validate
```



## Issue: The docker image does not contain the Jenkins Pipeline plugin I am using
You can add your plugin id to *plugins.txt* and build your own image. If you belive the plugin should be in this distributed image please make a PR or message me, I am happy to add more.
