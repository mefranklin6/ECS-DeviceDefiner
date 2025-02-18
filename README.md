# ECS-DeviceDefiner

GUI tool to define devices in your Extron ControlScript® (ECS) projects as JSON.

## Overview

![gui](https://github.com/user-attachments/assets/39d78626-9a1a-4dcd-9779-38140a420ecb)

The tool will convert the data you have entered into a JSON device definition file. The tool can then export this file to your processor.

This is the GUI tool used in [`Extron-Frontend-API`](https://github.com/mefranklin6/Extron-Frontend-API)

## Features

- Follows all ECS conventions**
- Pre-fills default values, as defined in the device classes.
- Input validation
- Intelligently 'greys out' fields that don't apply.  Ex: Username and Password only appear when EthernetClientInterface and SSH is selected.
- Preview pane for double checking before export or manual copy-paste.
- Export to the processor over SFTP.  Allows for file overwrite or appending.
- Pre-fill or add "select processor" buttons when running in an enviroment similar to `Extron-Frontend-API`

** The attribute `Alias` has been added for readability.  You can extend the extronlib device classes [as seen here](https://github.com/mefranklin6/Extron-Frontend-API/blob/main/src/extronlib_extensions.py), or you can ignore this attribute.

## Getting Started

1. Run this tool on a workstation with modern Python installed.  Optional: install `paramiko` for SFTP export if you don't have it already.

    ```powershell
    pip install -r requirements.txt
    ```

2. Fill out the fields ("Alias" is an added attribute which is just a "Friendly Name" to refer to the device).
3. Click `Generate and Add`.  Add more devices if needed.
4. When all devices are defined, click `Export over SFTP`.  Enter your processors IP or Hostaname and admin password.  If the file "/ports.json" on your processor already exists, you will be prompted to overwrite / append / cancel the operation.  
If you don't have paramiko installed or don't have a network route to your processor, you can click `Preview Export` and copy-paste from there.

## Using the JSON

For ideas on how to convert this JSON into fully instantiated devices automatically, check out [`Extron-Frontend-API`](https://github.com/mefranklin6/Extron-Frontend-API), particularly the `PortInstantiation` class in [`src/main`](https://github.com/mefranklin6/Extron-Frontend-API/blob/main/src/main.py)
