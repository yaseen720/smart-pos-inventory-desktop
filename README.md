<div align="center">
  <h1>📊 Smart POS & Inventory Management System (Advanced Desktop)</h1>
  <p><strong>Privacy-First Offline Desktop ERP with Scikit-Learn AI Demand Forecasting & CustomTkinter GUI</strong></p>

  <p>
    <img src="https://img.shields.io/badge/Platform-Windows_Desktop-0078D6?style=for-the-badge&logo=windows" alt="Platform Windows" />
    <img src="https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
    <img src="https://img.shields.io/badge/ML-Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-Learn" />
    <img src="https://img.shields.io/badge/Database-SQLite3_Encrypted-003B57?style=for-the-badge&logo=sqlite&logoColor=white" alt="SQLite" />
    <img src="https://img.shields.io/badge/Architecture-100%25_Offline_Privacy-darkgreen?style=for-the-badge" alt="Offline Privacy" />
  </p>

  <p>
    <a href="#-system-architecture">Architecture</a> •
    <a href="#-key-capabilities">Key Capabilities</a> •
    <a href="#-hardware--deployment-walkthrough">Hardware & Setup</a> •
    <a href="#-ai-demand-forecasting">AI Forecasting</a> •
    <a href="#-technical-stack">Tech Stack</a> •
    <a href="#-security--data-ownership">Security</a>
  </p>
</div>

---

> [!NOTE]
> **Commercial Software Notice**: This repository contains the public architecture blueprint, hardware case study, and technical documentation for the **Smart POS & Inventory Desktop Platform**. The underlying Python source code, proprietary ML weights, and database schemas are private and protected.

---

## 💡 Overview & Business Challenge

Most modern Point of Sale (POS) and inventory tools rely entirely on cloud SaaS subscriptions. For retail businesses, pharmacies, and supermarkets, this introduces significant risks:
1. **Internet Dependency**: In areas with unstable internet, checkouts freeze and sales stop.
2. **Data Privacy**: Customer purchase history and profit margins are stored on third-party cloud servers.
3. **Overstocking & Stock-Outs**: Store owners lack predictive tools to know when to reorder seasonal inventory.

### The Solution:
A standalone, high-performance desktop application engineered with **100% local data ownership**, sub-second barcode scanning, role-separated terminals (`Admin` vs `Cashier`), predictive machine learning for demand forecasting, and automated WhatsApp digital receipt dispatching.

---

## 🏗️ System Architecture

```mermaid
flowchart TD
    subgraph ClientHardware ["Hardware & Local Peripheral Layer"]
        Barcode["Laser Barcode / QR Scanner"]
        Terminal["Touchscreen POS Terminal"]
        Thermal["Receipt / WhatsApp Engine"]
    end

    subgraph DesktopUI ["CustomTkinter Modern Reactive GUI"]
        AuthView["Role Gatekeeper & PIN Auth<br/>(Admin / Cashier RBAC)"]
        POSView["High-Speed POS Checkout Terminal"]
        InvView["Real-Time Inventory CRUD & Low-Stock Alerts"]
        AnalyticsView["Matplotlib Trend Visualizer & Dashboards"]
        StaffView["HR, Salary Chronology & Staff Lifecycle"]
    end

    subgraph CoreEngine ["Embedded Python Logic & Analytics"]
        Forecasting["Scikit-Learn ML Engine<br/>(Time-Series Demand Forecasting)"]
        PandasEngine["Pandas Aggregator<br/>(Revenue, Margin & Sales Tracking)"]
        SecurityEngine["Local Cryptographic Vault<br/>(Bcrypt Hashing + Encrypted Backups)"]
        WhatsAppDispatch["Automated WhatsApp Receipt Service"]
    end

    subgraph DataStorage ["Privacy-First Data Layer"]
        SQLite[("Local SQLite3 Database<br/>Zero Cloud Leakage")]
        EncryptedBackup[("Encrypted Local Archives<br/>Automated Backup Vault")]
    end

    Barcode --> POSView
    Terminal <--> DesktopUI
    DesktopUI <--> AuthView

    POSView <--> PandasEngine
    InvView <--> SQLite
    AnalyticsView <--> PandasEngine
    AnalyticsView <--> Forecasting

    PandasEngine <--> SQLite
    Forecasting <--> SQLite
    SecurityEngine <--> EncryptedBackup
    POSView --> WhatsAppDispatch
