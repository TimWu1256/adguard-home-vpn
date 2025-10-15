# AdGuard Home + Tailscale

這個專案放了一個簡單的 Docker Compose 設定，整個系統架設在 Synology NAS 上。

在同個區網內，會同時啟動 AdGuard Home（提供 DNS 與廣告過濾）和 Tailscale（VPN）。

## 服務簡介

-   tailscale

    -   映像：`tailscale/tailscale`
    -   作用：把主機或容器加入 Tailscale 網路。
    -   資料存放：`./tailscale`

-   adguardhome
    -   映像：`adguard/adguardhome`
    -   作用：提供 DNS、廣告過濾等功能。
    -   資料存放：`./config`（設定）和 `./data`（運行資料）

## 快速啟動

在專案目錄下執行：

```powershell
# 啟動容器
docker compose up -d

# 查看日誌
docker compose logs -f tailscale
docker compose logs -f adguardhome
```

第一次啟動 Tailscale 可能需要授權節點（執行 `tailscale up` 並登入）。

通常可以用：

```powershell
docker exec -it tailscale tailscale up
```

AdGuard 的管理介面預設可以在 `http://localhost:8080` 找到。
