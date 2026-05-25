# TindaPOS

TindaPOS is a small sari-sari store point-of-sale web app backed by Google Sheets. It includes:

- fast product selection and cash/change checkout
- inventory editing and low-stock indicators
- daily sales and expense reporting
- installable offline-capable web interface
- demo mode stored locally until Google Sheets is connected

## Run The Web App

Serve this folder with any static file server, then open `index.html`. For example, with VS Code Live Server or:

```powershell
python -m http.server 8080
```

Open `http://localhost:8080`.

## Use Google Sheets As The Database

1. Create a blank Google Sheet.
2. Open **Extensions > Apps Script** from that sheet.
3. Replace the default script with the contents of `apps-script/Code.gs`.
4. Select `setupSheets`, click **Run**, and approve the Google permission prompts.
5. Click **Deploy > New deployment > Web app**.
6. Set **Execute as** to yourself and **Who has access** to anyone with the link.
7. Copy the `/exec` Web App URL.
8. In TindaPOS, open **Google Sheets Setup**, paste the URL, and click **Connect**.

When updating `apps-script/Code.gs` after an initial deployment, use **Deploy > Manage deployments > Edit**, create a **New version**, and deploy again before reconnecting the POS.

The script creates these sheets:

| Sheet | Purpose |
| --- | --- |
| `Products` | Product prices and available stock |
| `Sales` | Completed transactions and sale item JSON |
| `Expenses` | Daily expense records |

## Security Note

The Apps Script web-app URL grants access to write sales and inventory through the script. Keep the URL private and deploy it only for store devices you trust.
