>[Back to Week Menu](README.md)
>
>Previous Theme: [Model Selection Process](05_model_selection_process.md)
>
>Next Theme: [Introduction to NumPy](07_intro_numpy.md)

## Setting up the Environment
_[Original instructions](https://github.com/DataTalksClub/machine-learning-zoomcamp/blob/master/01-intro/06-environment.md)_

### Using GCP
1. Create **Virtual Machine** Instance (`Compute Engine` -> `VM Instances` -> `Create Instance`).
    ```
    Name: whatever name you would like to call this VM (ml-vm)
    Region, Zone: select a region near you, same with Zone (us-east1-b)
    Machine type: Standard, 4vCPu, 16 GB Memory (e2-standard-4)
    Operating system: Ubuntu
    Version: Ubuntu 20.04 LTS
    Boot disk size: 30Gb.
    ```
    When VM is created, note the external IP address.
2. Connect to created VM from terminal (Copy an external ip of created VM): 
    ```
    ssh -i ~/.ssh/gcp de_user@<external_ip_you_copied>
    ```
   You can also update or create a **config file** in your ~/.ssh folder, inputing the external IP address of your VM. This will allow you to just do `ssh ml-vm` to login to your VM
   ```
   $ cd ~/.ssh/
   # Create config file (or open if exists)
   $ touch config
   ```
   Add:
   ```
   Host ml-vm
    Hostname <external_ip_you_copied>
    User de_user
    IdentityFile ~/.ssh/gcp
   ```
   Then you can run `ssh ml-vm` to connect to this VM.
3. **Connect** to remote VM:
   ```
   ssh ml-vm
   ```
4. Update system:
   ```
    sudo apt-get update -y
    sudo apt-get upgrade -y
   ```
5. Install Anaconda:
    ```
    wget https://repo.anaconda.com/archive/Anaconda3-2023.07-0-Linux-x86_64.sh
    bash Anaconda3-2023.07-0-Linux-x86_64.sh -b
    rm Anaconda3-2023.07-0-Linux-x86_64.sh
    ```
6. Install Docker:
    ```
    sudo apt-get install -y docker.io
    ```
7. Give permission to run docker commands without sudo in VM:
    * Create file docker_without_sudo.sh:
        ```
        #!/bin/sh

        # Give permission to run docker commands without sudo in VM

        echo "=== Run docker_without_sudo.sh..."

        # 1. Add the docker group if it doesn't already exist
        echo "=== Add the docker group..."
        sudo groupadd docker

        # 2. Add the connected user $USER to the docker group
        # Optionally change the username to match your preferred user.
        echo "=== Add user $USER to the docker group..."
        sudo gpasswd -a "$USER" docker

        # 3. Restart the docker daemon
        echo "=== Restart the docker daemon..."
        if command -v service >/dev/null; then
        if [ "$(lsb_release -cs)" = "trusty" ] || [ "$(lsb_release -cs)" = "wily" ]; then
            sudo service docker.io restart
        else
            sudo service docker restart
        fi
        else
        sudo systemctl restart docker
        fi

        echo "=== IMPORTANT: Log out and log back in so that your group membership is re-evaluated."
        ```
    * Execute it:
        ```
        ./docker_without_sudo.sh
        ```
8. Install docker-compose:
    * Create file install_docker_compose.sh:
        ```
        #!/bin/bash

        # Install docker-compose

        echo "=== Run install_docker_compose.sh..."

        # Create a directory for executable files if it doesn't exist
        mkdir -p $HOME/bin

        # Download docker-compose into the bin directory
        echo "=== Download docker-compose..."
        wget https://github.com/docker/compose/releases/download/v2.16.0/docker-compose-linux-x86_64 -O $HOME/bin/docker-compose

        # Make docker-compose executable
        echo "=== Make docker-compose executable..."
        chmod +x $HOME/bin/docker-compose

        # Add the bin directory to the PATH variable if it's not already there
        echo "=== Make docker-compose visible from any directory..."
        grep -qxF 'export PATH="${HOME}/bin:${PATH}"' $HOME/.bashrc || echo 'export PATH="${HOME}/bin:${PATH}"' >> $HOME/.bashrc

        # Reload .bashrc
        echo "=== Reload .bashrc..."
        source $HOME/.bashrc
        ```
    * Execute it:
        ```
        ./install_docker_compose.sh
        ```
9. **IMPORTANT**: Log out and log back in so that your group membership is re-evaluated.

10. Create a condo environment with specific version of python (if needed):
    ```
    conda create -n py310 python=3.10 anaconda
    ```
    Activate this env:
    ```
    conda activate py310
    ```


_[Back to the top](#setting-up-the-environment)_