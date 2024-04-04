# Guide to Setting Up WSL2, Docker, and InfluxDB on Windows

## Check Windows Version

Before proceeding, it's crucial to ensure your system meets the necessary requirements.

1. **Check Version and Build Number**:
   - Press `Windows logo key + R`.
   - Type `winver` and press Enter.
   - Ensure your Windows version is **1903** or later. Update if it's not.
2. **Note for LTSC Windows Users**:
   - WSL2 is not available on LTSC versions of Windows.
   - Skip the WSL2 installation step and proceed to install Docker.
   - During Docker installation, choose **"Hyper-V"** instead of WSL2.

## Install and Update WSL2 via PowerShell

Windows Subsystem for Linux (WSL) allows you to run Linux distributions on Windows.

1. **Open PowerShell as Administrator**:

   - Right-click the Start button.
   - Select `Windows PowerShell (Admin)`.

2. **Enable WSL and Virtual Machine Platform**:

   - Execute:

     ```powershell
     dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
     dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
     ```

3. **Install WSL with Default Ubuntu Distribution**:

   - Run `wsl --install`.
   - Restart your computer.

4. **Update WSL**:

   - In PowerShell, execute `wsl --update`.
   - Restart if prompted.

5. **Set WSL to Version 2**:

   - Run `wsl --set-default-version 2`.
   - This sets WSL 2 as the default for new installations.

## Download and Install Docker Desktop for Windows

Docker is essential for running containerized applications.

1. **Download Docker Desktop**:
   - Download from Docker Desktop for Windows.
2. **Install Docker**:
   - Run the `Docker Desktop Installer.exe` file.
   - Follow the on-screen instructions.
   - Select **"Use WSL 2 instead of Hyper-V"** if applicable.
3. **Configure User Permissions**:
   - If your admin account differs from your user account, add your user to the `docker-users` group via Computer Management.

## Create a YAML File for InfluxDB Installation and Persistent Storage

The YAML file will define the configuration for your InfluxDB service.

1. **Create a New Folder**:

   - Name it "Docker" and place it in Documents.

2. **Create docker-compose.yml**:

   - Open a text editor.

   - Create a new file named `docker-compose.yml`.

   - Use the provided YAML content structure.

     ```yaml
     version: '3.8'
     
     services:
       influxdb:
         image: influxdb
         ports:
           - "8086:8086"
         volumes:
           - influx_data:/var/lib/influxdb
         restart: unless-stopped
         networks:
           - docker_network
     
       nodered:
         image: nodered/node-red
         ports:
           - "1880:1880"
         volumes:
           - node_red_data:/data
         restart: unless-stopped
         networks:
           - docker_network
     
     volumes:
       influx_data:
       node_red_data:
     
     networks:
       docker_network:
     ```

## Install InfluxDB via Docker

Using Docker to install and run InfluxDB simplifies the process.

1. Start InfluxDB Service:
   - Open PowerShell or Command Prompt where your `docker-compose.yml` file is.
   - Run `docker-compose up`.
   - InfluxDB will be accessible at `http://localhost:8086`.

## Set Up InfluxDB

Initial configuration of InfluxDB.

1. **Initial Setup**:
   - Go to `http://localhost:8086` for setup.
   - Create an initial user, organization, and bucket.
     - User: `bgdscada`
     - Password: Use Keepassxc to generate.
     - Organization: `projectnumber`
     - Bucket: `projectnumber`
2. **Secure Your Instance**:
   - Set a username and password.
   - Store the generated API token securely.

## Verify and Start Using InfluxDB

Begin utilizing InfluxDB for your data needs.

1. Start Using InfluxDB:
   - Once set up, explore InfluxDB for time-series data management.
   - Look into further configurations, querying data, or integration with other applications.

### 