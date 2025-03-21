# DNS Scans
One-liners for getting DNS information
## PowerShell
- Resolve Hostnames From Network Sweep
  - ```
    1..254 | %{Write-Host $(Resolve-DnsName -Name 192.168.40.$_ -LlmnrFallback -QuickTimeout -ErrorAction SilentlyContinue | select-object -Property NameHost, Name, Server, TTL | out-string) -NoNewLine}
    ```
  - Cons:
    - Takes a while to run
  - Pros:
    - Can give you an insight on what sort of devices are on your network
- Resolve Hostnames From Network Sweep using <em>ONLY</em> LLMNR and Netbios
  - ```
    1..254 | %{Write-Host $(Resolve-DnsName -Name 10.11.12.$_ -LlmnrNetbiosOnly -QuickTimeout -ErrorAction SilentlyContinue | select-object -Property NameHost, Name, Server, TTL | out-string) -NoNewLine}
    ```
    -Cons:
      - May get very limited information back
