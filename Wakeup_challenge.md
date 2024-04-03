Wakeup_challenge.md

## Network Ping Sweeper (Bash)

#### Use the first 3 sets of octets in the target IP range and then use {$num} command for last octet
 
    for num in {1..255}; do ping 10.0.2.$num -c 1; done | grep 64 | cut -d " " -f 4 | cut -d ":" -f 1 | tee ping_sweeper.txt

## Network Ping Sweeper (Python)

    import subprocess

    def ping_sweeper():
    """
    Ping sweeper function to ping all IP addresses in the range 10.2.6.1 to 10.2.6.255,
    filter out the IPs that have a successful ping response, extract the IP addresses,
    and save them to a file ping_sweeper.txt.
    """
    with open('ping_sweeper.txt', 'w') as f:
        for num in range(1, 256):
            ip_address = f'10.2.6.{num}'
            ping_process = subprocess.Popen(['ping', '-c', '1', ip_address], stdout=subprocess.PIPE)
            ping_output = ping_process.communicate()[0].decode('utf-8')
            if '64 bytes' in ping_output:
                ip = ping_output.split()[3].split(':')[0]
                f.write(ip + '\n')

    if __name__ == '__main__':