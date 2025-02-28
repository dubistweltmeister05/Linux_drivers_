# Custom Linux Device Drivers

## Overview
This repository contains a collection of custom Linux device drivers, primarily focusing on pseudo character drivers. These drivers are designed to demonstrate key Linux kernel programming concepts such as file operations, synchronization, and device interactions.

## Features
- **Hello World Driver**: Basic example to print messages in the kernel log.
- **Pseudo Character Driver**: Implementation of a simple character device driver.
- **Synchronization Mechanisms**: Example driver with proper locking mechanisms.

## Directory Structure
```
custom_drivers/
│── 001_hello_wrld/       # Basic Hello World driver
│── pseudo_char_drivers/  # Pseudo character device driver
│   ├── pcd.c             # Character driver implementation
│   ├── pcd_lock.c        # Driver with locking mechanism
│   ├── Makefile          # Build script
```

## Installation & Usage
### 1. Build the Drivers
Ensure you have the necessary Linux kernel headers installed, then compile the drivers using:
```sh
make
```

### 2. Load the Module
```sh
sudo insmod pcd.ko
```
Verify the module is loaded:
```sh
dmesg | tail
```

### 3. Create Device Node
```sh
sudo mknod /dev/pcd c <major_number> 0
```

### 4. Unload the Module
```sh
sudo rmmod pcd
```

## Dependencies
- Linux kernel headers
- GCC and Make

## License
This project is licensed under the MIT License.

## Contributing
Feel free to open issues and submit pull requests to enhance the drivers!
