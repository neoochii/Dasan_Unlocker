



### Step 1: Enter Recovery Mode

1. Power OFF the router.
2. Short the **RX** and **TX** test pads on the PCB.
3. Power ON or reboot the router while keeping RX and TX shorted.
4. Wait a few seconds for the device to enter recovery mode.
5. Remove the short.

---

### Step 2: Configure Static IP

Set your PC's Ethernet adapter to:

```text
IP Address : 192.168.1.100
Subnet Mask: 255.255.255.0
Gateway    : 192.168.1.1
```

---

### Step 3: Verify Recovery Mode

Open Command Prompt:

```cmd
ping 192.168.1.1
```

If the replies show:

```text
TTL=20
```

the router is in the correct recovery state and you can proceed.

---

### Step 4: Upload `tclinux.bin`

Open Command Prompt in the directory containing `tclinux.bin` and run:

```cmd
tftp -i 192.168.1.1 PUT tclinux.bin
```

Wait for the upload to finish.

The router should automatically reboot after processing the file.

---

### Step 5: Telnet Login

After the router reboots, connect using Telnet:

```cmd
telnet 192.168.1.1
```

Login credentials:

```text
Username: admin
Password: A!rTe7c / 1234 
```

---

### Step 6: Execute Commands

After logging in, run:

```sh
bootcfg customer DASAN
```

Then:

```sh
prolinecmd restore default
```

---

### Step 7: Reboot

Reboot the router:

```sh
reboot
```

or power cycle the device.

After reboot, the device should be initialized with the updated customer profile and default configuration.

---

## Troubleshooting

### Ping Does Not Show `TTL=20`

- Repeat the RX/TX shorting procedure.
- Verify the static IP configuration.
- Disable other network adapters.
- Try another Ethernet cable.

### TFTP Transfer Fails

- Ensure `tclinux.bin` is in the current directory.
- Verify the router responds at `192.168.1.1`.
- Temporarily disable the firewall if necessary.

### Telnet Login Fails

- Wait several minutes after reboot.
- Verify the device has completed booting.
- Repeat the procedure from recovery mode if required. 

AI is good btw
