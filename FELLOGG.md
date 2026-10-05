# Fellogg

En rad per fel.

| Nr | Vad stod i loggen? | Lokalt eller på GitHub? | Hur tog du reda på orsaken? | Hur löste du det? |
|----|--------------------|-------------------------|-----------------------------|-------------------|
| 1 | You have an error in your yaml syntax on line 11. | På GitHub Actions | Jämförde indragen i ci.yml och upptäckte ett extra mellanslag framför steget uv sync --frozen. | Tog bort mellanslaget så att alla steg under steps ligger på samma nivå. |
| 2 | Unable to find lockfile at uv.lock, but --frozen was provided. | På GitHub Actions | Loggen visade att uv.lock saknades. Med git check-ignore -v uv.lock såg jag också att filen ignorerades av .gitignore. | Skapade uv.lock med uv lock, tog bort regeln för uv.lock i .gitignore och lade till låsfilen i Git. |
| 3 | F401: os imported but unused i src/miniforecast/baseline.py. | På GitHub Actions | Ruff pekade på import os på rad 3 och visade att importen inte användes. | Tog bort import os och kontrollerade med uv run ruff check src tests. |
| 4 | Formateringskontrollen visade att baseline.py och test_baseline.py behövde formateras. | På GitHub Actions och lokalt | GitHub-loggen pekade på baseline.py och den lokala kontrollen på test_baseline.py. | Formaterade båda filerna med Ruff och kontrollerade med uv run ruff format --check src tests. |
| 5 | ModuleNotFoundError: No module named 'numpy'. | På GitHub Actions | Pytest-loggen visade att features.py importerade NumPy, som saknades i miljön. | Lade till NumPy med uv add numpy, vilket uppdaterade pyproject.toml och uv.lock. |
| 6 | test_moving_average_window_two misslyckades: förväntat första värde 1.5, men fick 1.0. | Lokalt | Läste moving_average och såg att koden delade med window + 1 i stället för window. | Ändrade nämnaren till window. Den efterföljande CI-körningen blev grön. |