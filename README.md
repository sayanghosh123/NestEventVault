# NestEventVault

**NestEventVault** is an open-source system for home users to automatically collect, store, and search Google Nest camera events in Azure. It provides a secure, reliable backend pipeline and a modern web dashboard for reviewing and searching events by date, type, and more.

---

## Features

- **Automated Event Collection**: Detects all supported events (motion, person, sound, etc.) from Google Nest cameras, even after migration to the Google Home app.
- **Azure Storage Integration**: Stores event metadata and snapshots (if available) in Azure Blob Storage.
- **Searchable Event Dashboard**: Web front end allows filtering and searching by date, month, year, event type, and keywords.
- **Secure & Private**: All credentials are securely managed; data is encrypted in transit and at rest.
- **Extensible**: Modular architecture for easy future enhancements.

---

## Architecture Overview

1. **Google Nest Device Access API**: Connects to your Nest cameras and streams event data via Google Cloud Pub/Sub.
2. **Backend Service**: Authenticates with Google, listens for events, normalizes data, and stores metadata and images in Azure.
3. **Event Index**: Metadata is indexed for fast search (using Azure Table Storage, Cosmos DB, or SQLite).
4. **Frontend Dashboard**: Modern web UI for searching, filtering, and reviewing events.

---

## Quick Start

### 1. Prerequisites

- Google (gmail.com) account
- Paid Device Access registration ([instructions](https://console.nest.google.com/device-access))
- Google Cloud Platform project with SDM API enabled
- Azure account with Blob Storage
- Node.js or Python (for backend)
- Modern browser (for frontend)

### 2. Setup Steps

#### Google Device Access

1. [Create a Google account](https://accounts.google.com/signup)
2. [Register for Device Access](https://console.nest.google.com/device-access) and pay the US$5 fee
3. [Create a Device Access Project](https://console.nest.google.com/device-access)
4. [Enable SDM API](https://console.cloud.google.com/apis/library/smartdevicemanagement.googleapis.com)
5. [Create OAuth 2.0 Credentials](https://console.cloud.google.com/apis/credentials)
6. [Link your Google account](https://developers.google.com/nest/device-access/account-linking)

#### Azure Storage

1. [Sign up for Azure](https://azure.microsoft.com/en-au/free/)
2. [Create a Blob Storage Account](https://portal.azure.com)
3. [Create a Storage Container](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-portal#create-a-container)
4. [Generate Storage Access Keys](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage)

#### Repository Setup

1. Clone this repo:
