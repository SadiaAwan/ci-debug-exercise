# Fellogg

En rad per fel. Skriv medan du minns hur du gjorde.

| Nr | Vad stod i loggen? | Lokalt eller på GitHub? | Hur tog du reda på orsaken? | Hur löste du det? |
|----|--------------------|-------------------------|-----------------------------|-------------------|
| 1  |You have an error in your yaml syntax on line 11|På GitHub : Actions |upptäckte ett extra mellanslag framför steget uv sync --frozenActionsActions | tog bort det extra mellanslaget så att alla steg under steps ligger på samma nivå.                                                         
| 2  |  Unable to find lockfile at uv.lock, but --frozen was provided  |På GitHub Actions |Loggen visade att uv.lock saknades när uv sync --frozen kördes.  |Skapade uv.lock med uv lock och lade till filen i Git.                |                         |                             |                   |
| 3  | F401: os imported but unused i src/miniforecast/baseline.py. | På GitHub Actions|  Ruff pekade på import os på rad 3 och angav att importen inte användes.|Tog bort import os och kontrollerade med uv run ruff check src tests. |                |                         |                             |                   |
|
Fortsätt tabellen med fler rader vid behov.
