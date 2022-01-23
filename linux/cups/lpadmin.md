- `lpadmin` configures printer and class queues provided by CUPS
  - `lpadmin -p CUPS-PDF -E` : enables a printer for printing and accepting jobs

# Install printer
- `lpadmin -p CUPS-PDF -v cups-pdf:/` : install a PDF printer
  - `-p` specifies printer
  - `-v` specifies device (in the form of device URI)
- `lpadmin -p CUPS-PDF -m "CUPS-PDF.ppd”` : Use a specific driver for a printer
- `apt install printer-driver-cups-pdf`
