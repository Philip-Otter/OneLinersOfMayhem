# Ping Sweeps
One-liners to locate network devices using ICMP Echo packets
## PowerShell
- Ping Sweep + TCP port check
  - ```
    1..254 | %{Write-Host $(Test-NetConnection -ComputerName 192.168.40.$_ -InformationLevel Detailed -port 3389 -ErrorAction SilentlyContinue -WarningAction SilentlyContinue| select-object -Property RemoteAddress, PingSucceeded, TcpTestSucceeded | out-string) -NoNewLine}
    ```
  - Cons:
    - Wicked slow
    - Flags as suspicious on Defender 365
  - Pros:
    - Able to target your search for devices that are running specific services on a standard port
  - ![image](https://github.com/user-attachments/assets/777e1b6d-ec3c-4b9f-bf3f-ede2d0f1a1c2)
- Standard Ping Sweep
  - ```
     1..254 | % {Write-Host $(('', "192.168.40.$_ RESPONDED!`n")[$(Test-Connection -Count 1 -ComputerName 192.168.40.$_ -quiet)]) -NoNewLine}
    ```
  - Cons:
    - Might miss a device that has a flaky connection
  - Pros:
    - Pretty Fast
  - ![image](https://github.com/user-attachments/assets/563a93ae-eab1-47e7-9fc3-d7900a7843fc)

