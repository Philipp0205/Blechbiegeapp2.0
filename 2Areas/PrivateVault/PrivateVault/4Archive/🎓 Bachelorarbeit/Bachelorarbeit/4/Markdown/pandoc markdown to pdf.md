pandoc -o example.pdf --from markdown --template eisvogel --listings example.md

pandoc --pdf-engine=xelatex --bibliography lib.bib --filter pandoc-citeproc --csl apa.csl -o example.pdf layout.yaml CitationTest.md

pandoc --from markdown --template eisvogel --pdf-engine=xelatex --bibliography lib.bib --filter pandoc-citeproc --csl apa.csl -o example.pdf example.md


# Layout
---
title:  'This is the title: it contains a colon'
mainfont: Arial
fontsize: 11pt
linestretch: 1
margin-left: 2.5cm
margin-right: 2.5cm

---

# To odt
pandoc -t odt file-name.md --reference-doc=path-to-your-file/reference.odt -o file-name.odt

pandoc -t odt --reference-doc=reference.odt --bibliography lib.bib --filter pandoc-citeproc --csl apa.csl -o output.odt 3_Forschungsmethode.md 
