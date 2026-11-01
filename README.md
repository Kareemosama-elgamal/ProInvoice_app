# ProInvoice — Professional Bilingual Invoice & Quotation Generator
منشئ الفواتير وعروض الأسعار الاحترافي ثنائي اللغة (العربية والإنجليزية)

**ProInvoice** is a production-quality, responsive client-side web application designed for freelancers, consultants, small businesses, and agencies. It allows users to quickly draft, preview in real time, and export beautiful A4 invoices and quotations as PDF or print documents, with full native support for Arabic (RTL) and English (LTR).

---

## 🌟 Key Features

1. **Complete Bilingual Support (Arabic & English):**
   - Instant language switching without page reloads or losing entered data.
   - True RTL layout for Arabic and LTR layout for English.
   - Connected Arabic typography (`Cairo` font) and clean Latin typography (`Inter`).
   - All labels, badges, summaries, and PDF print layouts are localized.

2. **Accurate Monetary Calculations:**
   - Integer minor-unit strategy (cents/halalas) prevents IEEE-754 floating-point inaccuracies.
   - Dynamic line items: add, edit, or remove rows with automatic real-time recalculation.
   - Supports line-level discounts and document-level discounts (percentage or fixed amount).
   - Tax/VAT support with **Exclusive (added)** and **Inclusive (in price)** calculation methods.
   - Tracks amounts paid and displays remaining balance due.
   - Clamps negative values and prevents corrupted calculations.

3. **Live A4 Document Preview:**
   - True-to-life A4 paper layout that updates instantaneously as you type.
   - Displays uploaded business logo, full company details, client information, itemized table, notes, payment/bank transfer info, and authorized signatory.

4. **Reliable PDF Export & Native Print:**
   - Exports clean, high-resolution A4 PDFs with readable vector text and properly shaped Arabic letters using `html2pdf.js` and HTML5 Canvas.
   - Built-in print CSS (`@media print`) for 1-click browser printing directly to PDF or physical printers.
   - Auto-generated standard filenames (e.g. `invoice-INV-2026-001.pdf` or `quotation-QUO-2026-001.pdf`).

5. **Local Persistence (Saved Documents & Business Profile):**
   - Saves business details (name, email, tax/VAT number, logo, default currency, bank accounts) in `localStorage`.
   - Save drafts, reopen previous documents, duplicate, or delete.
   - Filter documents by type (Invoice / Quotation), search by number or client name, and sort by date or amount.
   - Convert quotations to invoices with a single click.
   - Export full JSON backup or import backups safely.

6. **Privacy & Security First:**
   - 100% Client-Side. No external databases, no third-party tracking, and no customer data sent to remote servers.
   - Strict file type checking and size validation for logo uploads (PNG, JPG, SVG up to 1.5MB).
   - HTML sanitization against XSS.

---

## 📁 Project Structure

```text
d:\nafzly project\
├── index.html            # Main single-page application shell
├── css/
│   └── styles.css        # SaaS styling, responsive grid, A4 preview & print styles
├── js/
│   ├── app.js            # Main controller, state manager, and DOM binder
│   ├── calculations.js   # Precise financial calculation engine (minor units)
│   ├── i18n.js           # Bilingual dictionary & DOM translation manager
│   ├── storage.js        # LocalStorage persistence, backup export/import
│   └── pdf-service.js    # PDF generation wrapper with print fallback
├── vendor/
│   └── html2pdf.bundle.min.js # Bundled client-side PDF renderer
├── tests/
│   └── run-tests.js      # Automated unit & integration logic verification
├── server.js             # Zero-dependency local Node.js static web server
└── README.md             # Complete documentation
```

---

## 🚀 How to Run Locally

### Option 1: Using the Included Node.js Static Server (Recommended)
1. Open PowerShell or Command Prompt in the project folder:
   ```bash
   cd "d:\nafzly project"
   ```
2. Start the local server:
   ```bash
   node server.js
   ```
3. Open your browser and navigate to:
   **[http://localhost:3000](http://localhost:3000)**

### Option 2: Using Any Static Server
You can also serve this project using Python, VS Code Live Server, or Nginx:
```bash
# Python 3
python -m http.server 8080
```

---

## 🧪 Automated Testing & QA

Run the included automated test suite to verify math accuracy, discounts, tax handling, negative input safeguards, and dictionary completeness:

```bash
node tests/run-tests.js
```

### Verified Test Cases:
- [x] Single line item calculation (`quantity * price`).
- [x] Line item discounts.
- [x] Decimal quantities and prices without floating-point distortion.
- [x] Document-level percentage discount and fixed discount.
- [x] Tax calculation for both added (exclusive) and inclusive rates.
- [x] Amount paid and remaining balance due computation.
- [x] Negative input clamping and NaN handling.
- [x] 100% dictionary parity between Arabic and English.
- [x] Live A4 rendering and real-time preview updates.
- [x] Converting quotations into new invoices.
- [x] LocalStorage persistence and JSON backup import/export.

---

## 🌐 Static Hosting & Deployment

Because ProInvoice is completely serverless and client-side, you can deploy it for free to any static hosting provider:

- **Netlify / Vercel:** Drop the folder or connect your Git repository. Set publish directory to `.`.
- **GitHub Pages:** Push the files to a repository and enable GitHub Pages on the `main` branch.
- **Cloudflare Pages:** Connect repository and select direct static deployment.

---

## 📌 Limitations
- `localStorage` is scoped to the specific browser and device. If browser cache/data is cleared, saved invoices will be removed. Users are encouraged to click **Export Backup (JSON)** regularly.
- Very large images uploaded as logos should be optimized to avoid exceeding browser storage quotas (a 1.5MB safeguard is enforced).
