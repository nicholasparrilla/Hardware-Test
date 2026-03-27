# RF Test Automation with Python (PyVISA + SCPI)

This repository demonstrates a practical starting point for **RF test automation** using **Python**, **PyVISA**, and **SCPI**. It is structured like a small lab automation portfolio project: connect to instruments, identify them, configure basic measurement settings, and build toward repeatable RF workflows that are commonly used in hardware and test engineering projects.

## What this project covers

- Discovering VISA resources
- Connecting to instruments over USB, TCPIP, or GPIB
- Sending and querying SCPI commands
- Managing timeouts and communication settings
- Creating a safe workflow for first contact with lab equipment
- Using a mock instrument when hardware is not available

## Architecture

```text
Python -> PyVISA -> VISA backend (NI-VISA or pyvisa-py) -> Instrument transport -> SCPI commands
```

Where:

- **PyVISA** is the Python API used to open and talk to instruments
- **VISA backend** is the implementation layer that communicates with the operating system and instrument drivers
- **SCPI** is the command language supported by many instruments
- **Transport** may be TCPIP, USB, or GPIB depending on the setup

## Common troubleshooting points

### No resources found
- Check cables, power, and network connectivity
- Confirm the VISA backend is installed
- Try `pyvisa-py` first for simple setups, or NI-VISA for broader support

### Timeout on `*IDN?`
- Increase timeout
- Verify read and write termination characters
- Confirm the instrument is actually listening on the selected interface

### Resource opens but commands fail
- Check the vendor SCPI programming guide
- Some instruments need slightly different commands or subsystem paths
- Some interfaces require a different VISA resource string than expected
