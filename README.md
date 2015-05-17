# Ansible Role: Composer

[![MIT License](http://img.shields.io/badge/license-MIT-003399.svg)](http://opensource.org/licenses/MIT)

An Ansible role that manages an Iptables Firewall on Ubuntu 14.04

## Requirements

None

## Role Variables

`firewall_policy_input` sets the default policy for the INPUT chain:

    firewall_policy_input: "DROP"

`firewall_policy_forward` sets the default policy for the FORWARD chain:

    firewall_policy_forward: "DROP"

`firewall_policy_output` sets the default policy for the OUTPUT chain:

    firewall_policy_output: "ACCEPT"

`firewall_log_dropped_packets` flags whether dropped packets should be logged:

    firewall_log_dropped_packets: true

`firewall_ssh_port` sets an open port for SSH traffic

    firewall_ssh_port: 22

`firewall_allowed_tcp_ports` is a list of open TCP ports:

    firewall_allowed_tcp_ports: [80, 443]

`firewall_allowed_udp_ports` is a list of open UDP ports:

    firewall_allowed_udp_ports: []

`firewall_forwarded_tcp_ports` is a list of forwarded TCP ports. Each element
in the list may designate:

* **src** *required* The source port
* **dest** *required* The destination port

    firewall_forwarded_tcp_ports: []

`firewall_forwarded_udp_ports` is a list of forwarded UDP ports. Each element
in the list may designate:

* **src** *required* The source port
* **dest** *required* The destination port

    firewall_forwarded_udp_ports: []

`firewall_additional_rules` is a list of additional Iptables rules added
verbatim. For example: `firewall_additional_rules: ["iptables -A OUTPUT -f -d 192.168.1.1 -j DROP"]`

    firewall_additional_rules: []

## Dependencies

None

## Example Playbook

    ---
    - hosts: all
      vars:
      - firewall_ssh_port: 2222
      - firewall_allowed_tcp_ports: [80, 32400]
      roles:
      - novuso.firewall

## License

This is released under the [MIT license](http://opensource.org/licenses/MIT).
