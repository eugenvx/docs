---# Ultima încercare: înlocuire completă a caracterelor non-ASCII cu echivalente ASCII
def full_ascii(text):
    return remove_accents(text).encode("ascii", "ignore").decode("ascii")

# Refacem PDF-ul complet curățat
pdf = FPDF()
pdf.add_page()
pdf.set_auto_page_break(auto=True, margin=15)
pdf.set_font("Arial", size=10)

pdf.cell(200, 10, txt=full_ascii("DLT_VERGHE_MANIFEST_EXTINS_v1.0"), ln=True, align="C")
pdf.ln(5)

for key, value in manifest.items():
    if isinstance(value, dict):
        pdf.set_font("Arial", "B", 10)
        pdf.cell(200, 10, txt=full_ascii(f"{key}:"), ln=True)
        pdf.set_font("Arial", size=10)
        for subkey, subval in value.items():
            pdf.multi_cell(0, 10, txt=full_ascii(f"  {subkey}: {subval}"))
    else:
        pdf.multi_cell(0, 10, txt=full_ascii(f"{key}: {str(value)}"))
    pdf.ln(2)

pdf.set_font("Arial", "B", 10)
pdf.cell(200, 10, txt=full_ascii("Semnatura Digitala:"), ln=True)
pdf.set_font("Arial", size=10)
pdf.multi_cell(0, 10, full_ascii(semnatura_digitala))
pdf.ln(2)

pdf.set_font("Arial", "B", 10)
pdf.cell(200, 10, txt=full_ascii("Cheie Publica Ed25519:"), ln=True)
pdf.set_font("Arial", size=10)
pdf.multi_cell(0, 10, full_ascii(cheie_publica_ed25519))

# Salvare finală PDF
pdf_path = "/mnt/data/DLT_VERGHE_MANIFEST_EXTINS_v1.0.pdf"
pdf.output(pdf_path)

pdf_path
title: Working with forks
intro: 'Forks are often used in open source development on {% data variables.product.github %}.'
redirect_from:
  - /github/collaborating-with-issues-and-pull-requests/working-with-forks
  - /articles/working-with-forks
  - /github/collaborating-with-pull-requests/working-with-forks
versions:
  fpt: '*'
  ghes: '*'
  ghec: '*'
topics:
  - Pull requests
children:
  - /about-forks
  - /fork-a-repo
  - /about-permissions-and-visibility-of-forks
  - /configuring-a-remote-repository-for-a-fork
  - /syncing-a-fork
  - /allowing-changes-to-a-pull-request-branch-created-from-a-fork
  - /what-happens-to-forks-when-a-repository-is-deleted-or-changes-visibility
  - /detaching-a-fork
---
