# Nahan Project - User Guide

This guide walks you through the steps to access, configure, and manage your "Nahan" network gateway.

## 1. Accessing the Management Dashboard

Your management dashboard is located at `/sync/dash` by default.
To open it, open your browser and navigate to the following address:
`https://<YOUR_WORKER_DOMAIN>/sync/dash`

*(Note: If you open the main domain address or the `/sync` path without the WebSocket identifier in the browser, the system will automatically camouflage and load disguise sites like Ubuntu or Docker to mislead network scanners).*

## 2. Authentication

Upon accessing the dashboard, you will be greeted with a login page.
*   **Default Master Key:** `admin`
*   Enter the word `admin` and click the **Authenticate** button.

*(If you see a red warning message "⚠️ IOT_DB space not found!", it means you have not connected the D1 database to your worker in the Cloudflare panel. Make sure to establish this connection in Cloudflare before saving any changes).*

## 3. Dashboard Sections

The dashboard consists of the following main sections:

### 📡 Endpoints (Connections)
In this section, you can retrieve your connection links to import into client applications.
*   **Profile Cards:** Your profiles (default and added users) are displayed as separate cards.
*   **Show QR Code:** Clicking the **Show QR Code** button on any card opens a window with a QR code that you can scan with your phone.
*   **Cloud Sync URL (Sub Link):** A unified subscription link to fetch all configurations simultaneously. A copy button is available for quick copying.

### 👥 Users Management
A user management system with precise tracking of bandwidth and expiration dates:
*   **Add User:** Set traffic limits (in GB) and validity days for each new user.
*   **Pause User:** You can temporarily suspend a specific user's access by clicking the ⏸️ button.
*   **Subscription Links and QR:** Ability to get a dedicated subscription link for each user.

### 📊 Metrics (Network Status)
Displays information about the Cloudflare Edge node your traffic is passing through.
*   **Server Details:** Shows the origin IP, the processing Edge node (Colo), and geographic location.
*   **Network Latency Diagnostics:** By clicking "Run Diagnostics", you can measure your browser's real-time latency (ping) to the entered clean IPs.

### ⚙️ System (Basic Settings)
Configure the server's identity and core behaviors:
*   **Display Protocol:** Switch between Alpha (VLESS), Beta (Trojan), or **Both** (both concurrently in the sub link) modes.
*   **Unique Identifier (UUID):** Your connection password or identifier. If left blank, the system generates an automatic ID.
*   **Secret API Route:** Change the dashboard login path and subscription address. This changes your login address to `/<secret-path>/dash`.
*   **Master Key:** Change the dashboard login password from `admin` to a secure phrase.
*   **Backup & Restore:** Save current settings to a local `.json` file or load a previous backup file.

### 🌐 Advanced
Optimize network connection details and integrations:
*   **Clean IPs:** Enter a list of Cloudflare clean IPs (one IP per line). The subscription link automatically combines and multiplies configurations with these values.
*   **Slave Nodes:** If you have created other workers on different domains besides this panel, enter their links here separated by commas (`,`) (e.g., `node1.domain.com, node2.domain.com`). 
The main panel automatically synchronizes all changes and users with them and includes their configurations in the subscription link!
*   **Telegram Bot:** Enter your bot token and ID to receive dashboard login alerts and manage remotely with `/status`, `/users`, and `/pause` commands.
*   **Emergency Kill Switch:** A button to immediately cut off all proxy traffic.

### 📋 Logs (Activity Report)
*   View the history of recent login attempts and configuration changes.

## 4. Saving Configurations

After making changes in the **System** or **Advanced** sections:
1. Click the blue **Update Config** button at the bottom of the page.
2. The status will change to "Saving...", and the page will automatically refresh.
3. *Important:* If you modified the **Secret API Route**, the page will automatically redirect to the new address. Make sure to bookmark the new address in your browser.
