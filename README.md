```ascii
                    ┌───────────────────────┐
                    │     ╔═══╗ ╔═══╗       │
                    │  ╔══╣   ║ ║   ╠══╗    │
                    │  ║  ╚═══╝ ╚═══╝  ║    │
                    │  ║ ┌─────────┐   ║    │
                    │  ║ │  LINUX  │   ║    │
                    │  ║ │ DEVICE  │   ║    │
                    │  ║ │DRIVERS  │   ║    │
                    │  ║ └─────────┘   ║    │
                    │  ╚═══════════════╝    │
                    └───────────────────────┘
```

# 🚀 Custom Linux Device Drivers

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Kernel](https://img.shields.io/badge/Linux%20Kernel-5.x-blue.svg)](https://www.kernel.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

> 🔧 A collection of educational Linux kernel device drivers showcasing various kernel programming concepts and best practices.

```ascii
     .---.
    /     \
    \.@-@./
    /`\_/`\
   //  _  \\
  | \     )|_
 /`\_`>  <_/ \
 \__/'---'\__/
```

## 🌟 Features

- 🎯 **Hello World Driver**: Perfect starting point for kernel module development
- 💾 **Pseudo Character Driver**: Complete implementation with file operations
- 🔒 **Synchronization Example**: Thread-safe driver with proper locking mechanisms
- 📚 **Educational Resource**: Well-documented code with detailed comments

```ascii
    .─────────.
   /  ╭───╮   \
  /   │   │    \
 │    │   │     │
 │    ╰───╯     │
  \     ○      /
   `.       ,'
     `─────'
```

## 📁 Project Structure

```bash
custom_drivers/
├── 001_hello_wrld/          # Basic kernel module example
│   ├── hello.c              # Hello world driver implementation
│   └── Makefile            # Build configuration
│
├── pseudo_char_drivers/     # Character device implementations
    ├── pcd.c               # Basic character driver
    ├── pcd_lock.c          # Thread-safe character driver
    └── Makefile           # Build configuration
```

```ascii
     ┌─────────────┐
     │ ┌─┐ ┌─┐ ┌─┐ │
     │ │ │ │ │ │ │ │
     │ ├─┤ ├─┤ ├─┤ │
     │ └─┘ └─┘ └─┘ │
     └─────────────┘
```

## 🚀 Quick Start

### Prerequisites

```bash
# Ubuntu/Debian
sudo apt-get install build-essential linux-headers-$(uname -r)

# CentOS/RHEL
sudo yum groupinstall "Development Tools"
sudo yum install kernel-devel kernel-headers
```

### Building the Drivers

```bash
# Clone the repository
git clone https://github.com/dubistweltmeister05/custom_drivers.git
cd custom_drivers

# Build all drivers
make

# Build specific driver
cd pseudo_char_drivers
make
```

### Loading a Driver

```bash
# Load the module
sudo insmod pseudo_char_drivers/pcd.ko

# Verify loading
dmesg | tail

# Create device node (replace X with major number from dmesg)
sudo mknod /dev/pcd c X 0
sudo chmod 666 /dev/pcd

# Test the device
echo "Hello, Kernel!" > /dev/pcd
cat /dev/pcd
```

### Unloading a Driver

```bash
sudo rmmod pcd
rm /dev/pcd
```

```ascii
    ⚡ USAGE ⚡
   ┌─────────┐
   │ ▀ ▀ ▀ ▀ │
   │ ▀ ▀ ▀ ▀ │
   │ ▀ ▀ ▀ ▀ │
   └─────────┘
```

## 💡 Usage Examples

### Hello World Driver

```c
// Write to kernel log
echo "Hello from userspace" > /dev/kmsg
dmesg | tail

// Expected output:
// [    7.123456] Hello World driver initialized
```

### Pseudo Character Driver

```c
// Write operation
echo "Test data" > /dev/pcd

// Read operation
cat /dev/pcd

// IOCTLs (using provided test program)
./pcd_test --ioctl CMD_GET_SIZE
```

```ascii
    ╔════════╗
    ║ DEBUG  ║
    ╠════════╣
    ║▓▓▓▓▓▓▓▓║
    ║▓▓▓▓▓▓▓▓║
    ╚════════╝
```

## 🔍 Driver Details

### Hello World Driver

- Basic kernel module initialization
- Demonstrates module parameters
- Shows kernel log messaging

### Pseudo Character Driver

- Implements standard file operations (open, read, write, close)
- Demonstrates kernel memory management
- Includes IOCTL commands for device control
- Features proper error handling

### Thread-safe Driver

- Implements mutex locking
- Demonstrates atomic operations
- Shows proper synchronization techniques

```ascii
   < DEVELOP >
    ---------
    ^__^
    (oo)\_______
    (__)\       )\/\
        ||----w |
        ||     ||
```

## 🛠️ Development

### Debugging Tips

1. Use `dmesg` for kernel messages:

   ```bash
   dmesg -w
   ```

2. Check module information:

   ```bash
   modinfo pcd.ko
   ```

3. List loaded modules:
   ```bash
   lsmod | grep pcd
   ```

### Common Issues

- **Error: Module not found**

  - Ensure you're in the correct directory
  - Check if module is already loaded
  - Verify kernel version compatibility

- **Permission denied**
  - Run commands with sudo
  - Check device node permissions
  - Verify SELinux/AppArmor settings

```ascii
     .---.
    |   |
    |   |
    |   |
    |   |
   .' + '.
  '   |   '
 *    |    *
  '. _|_ .'
     |=|
     |=|
     |=|
     "-"
```

## 📚 Learning Resources

- [Linux Kernel Documentation](https://www.kernel.org/doc/html/latest/)
- [Linux Device Drivers, 3rd Edition](https://lwn.net/Kernel/LDD3/)
- [Kernel Newbies](https://kernelnewbies.org/)

```ascii
    Thank You!
   ┌─────────┐
   │ ^     ^ │
   │  \   /  │
   │   \ /   │
   │    *    │
   └─────────┘
```

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⭐ Show Your Support

Give a ⭐️ if this project helped you!

## 📧 Contact

Kshitij Vaze - [@VazeKshitij](https://x.com/VazeKshitij)

Project Link: [https://github.com/dubistweltmeister05/custom_drivers](https://github.com/dubistweltmeister05/custom_drivers)

---

<p align="center">Made with ❤️ for the Linux kernel community</p>
