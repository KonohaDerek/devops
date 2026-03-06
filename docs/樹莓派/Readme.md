1. 安裝 WireGuard
首先，需要安裝 WireGuard。您可以使用以下命令：

bash
複製程式碼
sudo apt update
sudo apt install wireguard resolvconf vim -y
2. 配置 WireGuard 客戶端
創建 WireGuard 配置文件。例如，可以將其命名為 /etc/wireguard/wg0.conf。這是配置文件的示例：

ini
複製程式碼
[Interface]
PrivateKey = <你的私鑰>
Address = 10.0.0.2/24
DNS = 8.8.8.8

[Peer]
PublicKey = <服務器的公鑰>
Endpoint = <服務器的IP或域名>:<服務器的端口>
AllowedIPs = 0.0.0.0/0, ::/0
PersistentKeepalive = 25
將 <你的私鑰> 和 <服務器的公鑰> 替換為實際的密鑰，並將 <服務器的IP或域名> 和 <服務器的端口> 替換為實際的服務器信息。

3. 啟用 WireGuard 客戶端
手動啟動 WireGuard 客戶端以確保配置正確：

bash
複製程式碼
sudo wg-quick up wg0
要停止 WireGuard 客戶端，可以使用：

bash
複製程式碼
sudo wg-quick down wg0
4. 設置開機自啟動
要在系統啟動時自動啟動 WireGuard 客戶端，請執行以下步驟：

bash
複製程式碼
sudo systemctl enable wg-quick@wg0
這將創建一個 systemd 服務，它會在系統啟動時自動啟動 WireGuard 客戶端。

5. 驗證配置
重新啟動 Raspberry Pi，並驗證 WireGuard 客戶端是否已啟動並正在運行：

bash
複製程式碼
sudo reboot
重新啟動後，可以使用以下命令驗證 WireGuard 客戶端的狀態：

bash
複製程式碼
sudo wg
這將顯示 WireGuard 客戶端的當前狀態，包括已連接的對等端和流量統計信息。

通過這些步驟，您可以確保 Raspberry Pi 在每次啟動時自動啟動 WireGuard 客戶端並連接到 VPN。