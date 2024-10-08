# MagicRecon: Automated Reconnaissance for Penetration Testing

<br>

`MagicRecon` is an advanced, easy-to-use tool designed to streamline and automate the reconnaissance phase of penetration testing. It enables security professionals to efficiently gather critical information about their target environment, ensuring a comprehensive overview of potential attack vectors.

<br>

With `MagicRecon`, you can:

- **Automate Information Gathering:** Quickly identify open ports, services, subdomains, and other critical data points.
- **Run Multiple Recon Tools:** Automatically execute a series of reconnaissance tools including Nmap, FFUF, Feroxbuster, and Netexec.
- **Filter and Process Results:** Identify and process only relevant web services while excluding known non-useful HTTP ports.

<br>

## Usage

To run `MagicRecon`, you need to provide a target IP address or hostname. The tool will then execute the reconnaissance tools on the target and generate output files for each tool.

<br>

### Basic Command

```bash
./MagicRecon <target> [<vhost>]
```

- **`<target>`**: The IP address or hostname of the target you want to scan.
- **`<vhost>`**: The vhost of the target you want to scan. This parameter is optional but required for vhost-based subdomain enumeration.

### Options

- **`-h`, `--help`**: Show this help message and exit.

### Example

```bash
./MagicRecon 10.10.11.22 blazorized.htb
```
=> run MagicRecon under your own user. Do not run as root, sudo will get used internally.

<br>
This command will:

1. **Run an Nmap Scan:** Perform a comprehensive scan of the target to identify open ports and services.
2. **Identify Web Server Ports:** From the Nmap results, it will determine which ports are running web servers (HTTP/HTTPS) and exclude certain non-useful HTTP ports (5357 and 5985).
3. **Run FFUF and Feroxbuster:** Execute web directory scanning tools (`ffuf` and `feroxbuster`) on identified web server ports.
4. **Run CrackMapExec:** Perform a CrackMapExec scan to enumerate SMB shares on the target.

<br>

### Notes

- **Permissions:** Some tools require root or administrative privileges to run. Ensure you have the necessary permissions before executing the script.
- **Dependencies:** The script relies on several external tools (`nmap`, `ffuf`, `feroxbuster`, and `crackmapexec`). Make sure these tools are installed and properly configured on your system.
- **Default Wordlists:** The script uses default wordlists for `ffuf` and `feroxbuster`. You can customize these if needed.

<br>

## License

MagicRecon is licensed under the GNU GENERAL PUBLIC LICENSE Version 3. See the [LICENSE](LICENSE) file for details.

<br>

## Contributing

Contributions to MagicRecon are welcome! Please see the [CONTRIBUTING](CONTRIBUTING.md) file for more information on how to contribute.
