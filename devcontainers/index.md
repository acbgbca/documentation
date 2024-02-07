# Documentation

https://containers.dev/

# Troubleshooting

## Error finding Java

VSCode uses inheritance for the settings, and so if the host PC defines the Java location it will try and us it in the container. To override, add the following section to devcontainer.json:

```json
	"customizations": {
		// Configure properties specific to VS Code.
		"vscode": {
			// Set *default* container specific settings.json values on container create.
			"settings": { 
				"java.configuration.runtimes": [
					{
						"name": "JavaSE-17",
						"path": "/usr/lib/jvm/msopenjdk-current"
					}
				]
			}
        }
    }
```

Set the name based on the version you are using. Confirm that path matches what is used by the Dev Container