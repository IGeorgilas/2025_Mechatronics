
## To check that all boards are communicating over I2C

You connect toq the Raspberry Pi via SSH and run:

```
i2cdetect -y 1
```
and you expect to see something like this (example with all boards connected):

```
    0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:                         -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- 1e -- 
20: -- -- -- -- -- -- -- -- -- -- 2a -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- 48 -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- 68 -- -- 6b -- -- -- -- 
70: -- -- -- -- -- -- -- --                         
```
                         
## Running any of the scripts (.sh) on a Raspberry Pi

To run the script you need:

1) Have the Raspberry Pi connected (power and network).

2) Open a Terminal (Mac) or a Command Prompt (Windows) and copy the script to the Pi:
```
scp ./<script_name>.sh pi@<raspberry_pi_address>:~/<script_name>.sh
```

3) SSH to the Raspberry Pi and make the script executable:
```
ssh pi@<raspberry_pi_address>
chmod +x ~/<script_name>.sh
```

4) Run the script:
```
./<script_name>.sh
```

In case of errors due to encoding (usually becasue the script was edited on Windows), you can convert the file to Unix format using:

```
sed -i 's/\r$//' ~/<script_name>.sh
```

Notes:
- Replace `<raspberry_pi_address>` with the Pi’s IP or hostname (e.g., `raspberrypi.local`).
- On Windows, `scp`/`ssh` are available if OpenSSH is installed (Windows 10/11).
- The script uses `i2cget/i2cset`; ensure I2C is enabled on the Pi and `i2c-tools` is installed. It is by default on Raspberry Pi if the Matlab Support Package for Raspberry Pi is installed.