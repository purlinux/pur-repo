# Official Pur Repository
## Adding repository to your local system
Pur uses environment variables to determine the paths for repositories, if this environment variable is not present it will use 3 default paths:
* /usr/repo/pur/ 
* /usr/repo/pur-community/
* /usr/repo/unofficial

If you want to add more repositories, you should also add these to the environment variable. Example of using environment variables for declaring your own local repositories:


```sh
#!/bin/sh
export PUR_PATH="/usr/repo/pur"
PUR_PATH="$PUR_PATH:/usr/repo/pur-community"
PUR_PATH="$PUR_PATH:/usr/repo/unofficial"
PUR_PATH="$PUR_PATH:/foo/bar"
```

## Creating your own repository
You can create your own repository, either locally, version controlled, or published in what way you may want. You can declare your own way of updating the repository within the `update` script. This file does not have to be present, as it will simply skip updating the repository if it is not present. However, it will not automatically detect repositories, so if you do want it to update; declare it manually. 

Example of an `update` script for GIT repositories:

```sh
#!/bin/sh
git pull origin $(git branch --show-current) # this will simply pull from the current used branch upon `pur update`.
```

Creating local changes of repositories is not recommended, as these changes will be overriden once there's a new update to the origin repository. This does not apply if the repository is merely local and not version controlled.

## Contributing to the official PUR repository 
The official Pur (not to be confused with the [PUR](https://github.com/purlinux/pur-user-repository)) is merely reserved for base components for systems. If there any issues with the packages, or there are packages which should be added here, feel free to create a pull request, or create an issue if you are not able to fix the package yourself. But generally, if you want to add misc packages, you should submit them to the [PUR](https://github.com/purlinux/pur-user-repository).
