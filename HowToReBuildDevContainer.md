# Adding Preinstalled Extensions to a Dev Container

To add extensions to your dev container configuration, you'll need to modify your `devcontainer.json` file. Here's how to specify extensions in your separate Git repo:

## Method 1: Directly in `devcontainer.json`

1. Open/Create your `.devcontainer/devcontainer.json` file
2. Add the `extensions` property with your desired extensions:

```json
{
  "name": "Your Container Name",
  "extensions": [
    "ms-python.python",
    "ms-vscode.vscode-typescript-next",
    "dbaeumer.vscode-eslint",
    "eamodio.gitlens",
    "esbenp.prettier-vscode",
    "visualstudioexptteam.vscodeintellicode",
    "ms-azuretools.vscode-docker"
  ]
}
```

## Method 2: Using a Feature (for more complex setups)

If you need more control, you can create a custom feature:

1. Create a `features` directory in your `.devcontainer` folder
2. Add a JSON file for your extensions (e.g., `my-extensions.json`):

```json
{
  "id": "my-extensions",
  "version": "1.0.0",
  "customizations": {
    "vscode": {
      "extensions": [
        "ms-python.python",
        "ms-vscode.vscode-typescript-next"
      ]
    }
  }
}
```

3. Reference it in your `devcontainer.json`:

```json
{
  "name": "Your Container",
  "features": {
    "my-extensions": {
      "version": "1.0.0"
    }
  }
}
```

## Finding Extension IDs

To find the correct extension IDs:
1. Open the extension in VS Code Marketplace
2. Look at the URL (e.g., `https://marketplace.visualstudio.com/items?itemName=ms-python.python` → ID is `ms-python.python`)
3. Or click the "Unique Identifier" in the extension details page

## After Configuration

Rebuild your container to apply the changes:
```bash
devcontainer rebuild --workspace-folder .
```

Would you like me to suggest specific extensions based on your development environment (e.g., Python, JavaScript, etc.)?