# Task

**Supported distributions:** Debian, Gentoo

Install ssh configuration for jump host on the network.

 * Create `~/.ssh/jumphosts` with jump host configuration files.
 * Include `~/.ssh/jumphosts/*` in the `/home/{user}/.ssh/config`
   configuration file.

# Dependencies

The 'Include' option used in the ssh configuration requires version 7.3p1 of
OpenSSH or above.

# Variables

 * **jumphost_dir**: Directory to save jump host configuration files. Directory
   is created in `~/.ssh/`.
   * *Default*: "jumphosts"

## Hosts

Each hosts jump host configuration is created using host variables. A
configuration for connecting to the current host through the jump host
alice@server.example.com:22 like this:

    jumphosts:
      server.example.com:
        users:
          - bob
        jhost_user: alice
        jhost_port: 22
        port: 22

Each entry start with the host name of the jump host, the dictionary values are
as follows:

 * **users**: Users on the current host where the jump host configuration file
   is installed.
 * **jhost_user**: Ssh user on the jump host.
 * **jhost_port**: Ssh port on the jump host.
 * **port**: Ssh port on the target machine.
