# Port Scanners
One-liners to scan those ports
## PowerShell
- The Poor Man's Port Scanner
  - ```
    1..56535 | %{Write-Host (('',"Port $_ UP!`n")[((New-Object System.Net.Sockets.TcpClient).ConnectAsync("192.168.40.1", $_).Wait(100))]) -NoNewLine}
    ```
  - Cons:
    - Flags as suspicious by Defender 365
  - Pros:
    - Adjustable speed
  - ![image](https://github.com/user-attachments/assets/13700154-1237-4c5b-b07d-11977bb81f5c)
