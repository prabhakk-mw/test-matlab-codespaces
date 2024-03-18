# Codespace based on mathworks/matlab DockerHub images 

The `.devcontainer/devcontainer.json` configuration showcases:

1. The usage of the `mathworks/matlab` image for a given release of MATLAB.
2. On Codespace startup, a browser tab will open from which you can:
    * Provide licensing information and 
    * Access MATLAB through the browser.
3. The installation of the MATLAB Extension for VSCode. (Does not work unless you are using a Network License Manager)


## Using the mathworks/matlab Docker Hub Image

Use this configuration file to start a devcontainer with MATLAB R2023b available within it.

```json
{
  "name": "MATLAB",
  "image": "mathworks/matlab:r2023b",
  "waitFor": "updateContentCommand",
  "updateContentCommand": {
    // installing GIT
    "install-git": "sudo apt-get update && sudo apt-get install git -y",
  },
}
```

### Run MATLAB and interact with it via a web browser

This configuration adds the capability to start [matlab-proxy](https://github.com/mathworks/matlab-proxy) and interact with MATLAB through the browser.
Use this configuration if you want to interact with the MATLAB Desktop through the browser.

```json
{
  "name": "MATLAB",
  "image": "mathworks/matlab:latest",
  "hostRequirements": {
    "cpus": 4
  },
  "portsAttributes": {
    "8888": {
      "label": "MATLAB",
      "onAutoForward": "openBrowser"
    }
  },
  "waitFor": "updateContentCommand",
  "updateContentCommand": {
    // installing GIT
    "install-git": "sudo apt-get update && sudo apt-get install git -y",
    "update-matlab-proxy": "sudo python3 -m pip install --upgrade pip matlab-proxy"
  },
  // Only works from R2022a onwards
  "postStartCommand": "run.sh -browser"
}
```

The `postStartCommand` and the `onAutoForward` start the `matlab-proxy` and open a browser tab.

* NOTE: Based on your systems configuration it may be necessary to click on the link presented in the VSCode terminal to start the browser session.

Click on [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://github.com/codespaces/new?hide_repo_select=true&ref=mathworks%2Fmatlab&repo=345968540&skip_quickstart=true&template=false&machine=standardLinux32gb&devcontainer_path=.devcontainer%2Fdevcontainer.json) to select the MATLAB release you would like to open on GitHub Codespaces.


---

Copyright 2024 The MathWorks, Inc.

---
