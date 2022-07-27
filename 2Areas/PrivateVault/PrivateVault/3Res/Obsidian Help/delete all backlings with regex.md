[[4Archive/daily_archive 1/2020/June/12-06-2020]]

# Command 
cat 4_Thematische_Eigenleistung_Ergebnisse.md | sed -e 's/\[\[.*\]\]//g' > output.md

better: \[\[[^]]*\]\]

# Problem 
- Leaves empty lines where the backlink was 